---
title: "Parche de MDVA-31640: no se puede crear una actualización programada consecutiva a través de la API de REST"
description: El parche de MDVA-31640 soluciona el problema de que no se puede crear una nueva actualización programada para el precio especial en varias tiendas mediante la API de REST, si la fecha de inicio de la actualización coincide con la fecha de finalización de la actualización anterior. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.
exl-id: 8d91db3d-7c94-4757-8087-4cf53cad81e7
feature: REST
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# Parche de MDVA-31640: no se puede crear una actualización programada consecutiva a través de la API de REST

El parche de MDVA-31640 soluciona el problema de que no se puede crear una nueva actualización programada para el precio especial en varias tiendas mediante la API de REST, si la fecha de inicio de la actualización coincide con la fecha de finalización de la actualización anterior. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 está instalado. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.5-p1

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.1 - 2.3.5-p2, 2.4.0, 2.4.0-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Corrige el problema en el cual no se puede crear una nueva actualización programada para el precio especial para varias tiendas mediante la API de REST, si la fecha de inicio de la actualización coincide con la fecha de finalización de la actualización existente anteriormente.

<u>Pasos a seguir</u>:

1. Configurar un sitio web, una tienda y una vista de tienda adicionales.
1. Cree dos productos simples: &quot;product1&quot; y &quot;product2&quot;.
1. Asigne product1 a un sitio web y product2 a ambos.
1. Cree una actualización programada para el precio especial del producto1 en la vista de tienda para la tienda con ID 1. Usar la API de REST `POST` solicitud a `rest/V1/products/special-price` con la siguiente carga útil:
   `{        "prices": [            {                "price": 15,                "store_id": 1,                "sku": "product1",                "price_from": "2021-11-15 04:00:00",                "price_to": "2021-11-15 04:10:00"            }        ]    }`
1. Cree una actualización programada para el precio especial del producto2 en ambas vistas de tienda para tiendas con ID 1 y 2 que utilicen la API de REST `POST` solicitud a `rest/V1/products/special-price` con la siguiente carga útil (la `price_from` la fecha es la misma que `price_to` fecha de la solicitud anterior):
   `{        "prices": [            {                "price": 14,                "store_id": 1,                "sku": "product2",                "price_from": "2021-11-15 04:10:00",                "price_to": "2021-11-15 04:15:00"            },            {                "price": 13,                "store_id": 2,                "sku": "product2",                "price_from": "2021-11-15 04:10:00",                "price_to": "2021-11-15 04:15:00"            }        ]    }`

<u>Resultados esperados</u>:

La actualización programada con el cambio de precio especial se crea en ambas vistas de tienda.

<u>Resultados reales</u>:

Adobe Commerce genera un error. No se ha creado la actualización programada.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
