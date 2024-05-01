---
title: "ACSD-47079: el estado de existencias de los productos compuestos no se actualiza cuando cambia el estado de existencias de subproductos"
description: Aplique el parche ACSD-47079 para corregir el problema de Adobe Commerce en el que el estado de las existencias de los productos compuestos (paquete, agrupados y configurables) no se actualiza cuando el estado de las existencias de subproductos cambia a través del POST de API de REST /rest/V1/inventory/source-items.
exl-id: 603e4548-fb04-43b4-a033-4f2c7f665fae
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-47079: el estado de las existencias de los productos compuestos no se actualiza cuando cambia el estado de las existencias de subproductos

El parche ACSD-47079 corrige el problema en el que el estado de stock de los productos compuestos (paquete, agrupados y configurables) no se actualiza cuando el estado de stock del subproducto se cambia a través del POST de API de REST `/rest/V1/inventory/source-items`. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 está instalado. El ID del parche es ACSD-47079. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El estado de stock de los productos compuestos (paquete, agrupados y configurables) no se actualiza cuando el estado de stock del subproducto se cambia a través del POST de API de REST `/rest/V1/inventory/source-items`.

<u>Pasos a seguir</u>:

1. Cree un producto configurable, agrupado y agrupado con un producto secundario simple para cada uno.
1. Defina cada estado de producto secundario simple en **[!UICONTROL Out of Stock]** uso del `source-items` Llamada de API.
1. Ahora, compruebe el estado de stock del producto principal.

<u>Resultados esperados</u>:

El estado del producto principal es [!UICONTROL Out of Stock].

<u>Resultados reales</u>:

El estado del producto principal es [!UICONTROL In Stock].

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
