---
title: 'MDVA-42341: "categoryList" La consulta GraphQL no filtra los resultados'
description: El parche MDVA-42341 resuelve el problema de que la consulta GraphQL categoryList no filtra los resultados si una solicitud tiene el encabezado Store. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8. El ID del parche es MDVA-42341. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: 34aeb30a-9491-4102-b33e-dcd857b6a1c2
feature: GraphQL, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-42341: &quot;categoryList&quot; La consulta GraphQL no filtra los resultados

El parche MDVA-42341 resuelve el problema de que la consulta GraphQL categoryList no filtra los resultados si una solicitud tiene el encabezado Store. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 está instalado. El ID del parche es MDVA-42341. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La consulta GraphQL categoryList no filtra los resultados si una solicitud tiene el encabezado Store.

<u>Pasos a seguir</u>:

1. Cree una nueva categoría raíz y asígnele el nombre **root2**.
1. Cree un segundo sitio web, tienda o tienda y asigne **root2** a la nueva tienda.
1. Cree una nueva categoría en Categoría raíz predeterminada = category1.
1. Con una solicitud de GraphQL, obtenga una lista de categorías para el segundo sitio web (utilice Tienda de encabezado = nuevo).

<pre>
<code class="language-graphql">
{
  categoryList(filters: {name: {match: "category1"}}) {
    uid
    level
    name
    breadcrumbs {
      category_uid
      category_name
      category_level
      category_url_key
    }
  }
}
</code>
</pre>

<u>Resultados esperados</u>:

Las categorías de la categoría raíz predeterminada no se enumeran como respuesta, ya que se utiliza un encabezado de tienda &quot;nuevo&quot;.

<u>Resultados reales</u>:

Las categorías de la categoría raíz predeterminada están disponibles en los resultados.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
