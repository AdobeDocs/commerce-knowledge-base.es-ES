---
title: "Parche MDVA-33975: cálculos de precios de GraphQL"
description: 'El parche MDVA-33975 soluciona los problemas de cálculo de precios de GraphQL. Estos problemas incluyen:'
exl-id: a8266334-72cb-4b50-9ff5-9a977d762e5c
feature: GraphQL, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Parche MDVA-33975: cálculos de precios de GraphQL

El parche MDVA-33975 soluciona los problemas de cálculo de precios de GraphQL. Estos problemas incluyen:

* Cuando se aplica una regla de precios de catálogo a un grupo de clientes determinado, los precios de los artículos en el carro de compras y el total del pedido no se calculan correctamente en GraphQL.
* Las reglas de precios de catálogo no están incluidas en `CartItemPrices` en la API.
* El precio de grupo del cliente para el cliente general no se agrega en la respuesta de consulta del producto de GraphQL.
* Volver a calcular los totales de las cotizaciones antes de responder sobre los precios provoca que se pierdan las reglas aplicadas.
* El descuento del importe de envío no se recuperó en el último paso de facturación y el total general se mostró incorrectamente.
* El descuento no se aplica en GraphQL cuando el segmento de cliente se utiliza en la condición de regla de precio de carro de compras.

Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.14 está instalado.

## Productos y versiones afectados

* El parche se ha diseñado para Adobe Commerce local 2.4.1.
* El parche también es compatible con las siguientes versiones de Adobe Commerce: Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.4 - 2.4.1.

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos, según el producto de Adobe Commerce:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en la herramienta QPT, consulte la [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
