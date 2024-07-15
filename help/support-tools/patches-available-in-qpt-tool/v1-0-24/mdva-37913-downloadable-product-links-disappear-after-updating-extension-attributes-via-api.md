---
title: "MDVA-37913: Los vínculos de descarga de productos desaparecen después de actualizar los atributos de extensión mediante la API"
description: El parche MDVA-37913 para resuelve el problema de que los vínculos de productos descargables desaparecen después de actualizar los atributos de extensión mediante API. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24. El ID del parche es MDVA-37913. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.
exl-id: e4b2cf59-5c35-4a28-a63e-15cd7d0d5a5d
feature: REST, Attributes, Extensions, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# MDVA-37913: Los vínculos de descarga de productos desaparecen después de actualizar los atributos de extensión mediante la API

El parche MDVA-37913 para resuelve el problema de que los vínculos de productos descargables desaparecen después de actualizar los atributos de extensión mediante API. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24. El ID del parche es MDVA-37913. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.


## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**
Adobe Commerce en infraestructura en la nube 2.3.6

**Compatible con versiones de Adobe Commerce:**
Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.0 - 2.4.0-p1
>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.


## Problema

Los vínculos de producto descargables desaparecen después de actualizar los atributos de la extensión mediante API.

<u>Requisitos previos</u>:
Producto descargable con vínculos de descarga.

<u>Pasos a seguir</u>:

1. Actualice los atributos de la extensión con una solicitud como esta:

```JSON
{
    "product": {
        "extension_attributes": {
            "stock_item": {
                "is_in_stock": true,
                "qty": 100
            }
        }
    }
}
```

<u>Resultados esperados</u>:<br>
El producto se ha actualizado y no se han eliminado todos los vínculos de descarga.

<u>Resultados reales</u>:<br>
El producto se ha actualizado, pero se han eliminado todos los vínculos de descarga.


## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html)

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad en nuestra base de conocimiento de asistencia, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Para obtener información sobre otros parches disponibles en la herramienta QPT, consulte la sección [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) de nuestra base de conocimiento de asistencia.
