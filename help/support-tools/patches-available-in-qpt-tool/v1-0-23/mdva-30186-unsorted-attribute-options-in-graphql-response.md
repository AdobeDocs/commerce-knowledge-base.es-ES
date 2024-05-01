---
title: "MDVA-30186: Opciones de atributo sin ordenar en la respuesta de GraphQL"
description: El parche MDVA-30186 resuelve el problema en el que las opciones de atributos no se ordenan en la respuesta de GraphQL. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23. El ID del parche es MDVA-30186. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.
exl-id: 7b2aef16-5012-4206-9444-e0b765f0c0c9
feature: Attributes, GraphQL, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-30186: Opciones de atributo sin ordenar en la respuesta de GraphQL

El parche MDVA-30186 resuelve el problema en el que las opciones de atributos no se ordenan en la respuesta de GraphQL. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 está instalado. El ID del parche es MDVA-30186. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce en la infraestructura en la nube 2.3.4 y 2.4.2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.4 - 2.3.5-p2, 2.4.0 - 2.4.0-p1 y 2.4.2 - 2.4.2-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir</u>:

1. Añada tres opciones al atributo de color existente.
1. Cree seis productos simples con opciones (Ejemplo: *Opción 1*: 1 producto, *Opción 2*: 2 productos, *Opción 3*: 3 productos).
1. Cree una categoría y asigne todos los productos creados anteriormente.
1. Ahora realice la siguiente solicitud de GraphQL con su ID de categoría:

   <pre><code class="language-graphql">
    {
      products(
        filter: { category_id: { eq: "3" } }
        pageSize: 200
        currentPage: 1
        sort: { name: ASC }
      ) {
        aggregations {
          attribute_code
          count
          label
          options {
            count
            label
            value
          }
        }
        items {
          name
          sku
          url_key
        }
      }
    }
    </code></pre>

1. Ahora, modifique el orden de las opciones de atributo desde la página de edición de atributos en Admin.
1. Vuelva a realizar la solicitud de GraphQL anterior y observe las opciones de atributos de color.

<u>Resultados esperados</u>:

Las opciones de atributos se ordenan según el orden establecido desde el Administrador.

<u>Resultados reales</u>:

Las opciones de atributos siempre se ordenan según el número de productos asociados.


## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
