---
title: "MDVA-33168: El extremo asincrónico de API anula el precio especial"
description: El parche MDVA-33168 corrige el problema en el que el uso del extremo asincrónico de la API para actualizar un atributo de producto anula el establecimiento de un precio especial.
exl-id: 4dd26215-b140-4924-8f4d-0d062e5fda2d
feature: REST, Orders, Personalization
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-33168: extremo asincrónico de API anula el precio especial

El parche MDVA-33168 corrige el problema en el que el uso del extremo asincrónico de la API para actualizar un atributo de producto anula el establecimiento de un precio especial.

Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 está instalado. El ID del parche es MDVA-33168. Tenga en cuenta que el problema está planificado para solucionarse en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.3-p1

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.3 - 2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir</u>:

1. Cree dos sitios web con tiendas.
1. Ir a **Tiendas > Configuraciones > Catálogo > Catálogo > Precio > Catálogo** y Establecer **Precios y alcance** = *Sitio web*.
1. Crear un *text-type* atributo de producto. Mantenga todas las opciones predeterminadas.
1. Agregue el atributo creado al conjunto de atributos predeterminado.
1. Cree un producto simple para utilizarlo con un producto agrupado.
1. Cree un paquete de producto con las siguientes opciones de ejemplo:
   * **Activar producto** = *Sí*.
   * **Conjunto de atributos** = *Predeterminado*.
   * **Nombre del producto** = *paquete-1*.
   * **SKU** = *paquete-1*.
   * **SKU dinámico** = *Sí*.
   * **Precio** = *100,00 $*.
   * **Clase de impuesto** = *Bienes gravables*.
   * **Estado de stock** = *En stock*.
1. En **Elementos de paquete**, establezca estas opciones de ejemplo:
   * **Enviar artículos agrupados** = *Juntos*.
   * **Título de opción** = *prueba*, **Tipo de entrada** = *Botones de opción*, **Requerido** checkbox = *comprobado*.
   * **Es predeterminado** checkbox = *desenfrenado*.
   * **Nombre** = *simple-100*.
   * **SKU** = *simple-100*.
   * **Precio** = *100,00*.
   * **Tipo de precio** = *Fijo*.
   * **Cantidad predeterminada** = *1*.
   * **Definido por el usuario** checkbox = *desenfrenado*.
1. Cambie el ámbito al almacén no predeterminado y establezca el precio especial. (Ejemplo: en el **Precios avanzados** página, establecer **Precio especial** = *4 %*, y **Vista de precios** = *Intervalo de precios*.)
1. Actualice el nuevo atributo solo en el ámbito de almacén no predeterminado, como en este ejemplo:

   ```php
       PUT {{base_url}}/rest/en_au/async/V1/products/{{sku}}    {        "product": {            "custom_attributes": [                {                    "attribute_code": "text_attr",                    "value": 21                                   }            ]                    }    }
   ```

<u>Resultados esperados</u>:

Otros valores de atributo permanecen igual al actualizar un atributo de producto mediante la API de REST asincrónica, según lo esperado.

<u>Resultados reales</u>:

Se elimina el precio especial, que se estableció mediante la API de REST asincrónica en el ámbito de la tienda.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
