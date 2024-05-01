---
title: "ACSD-53628: El informe de pedidos de ventas CSV muestra caracteres especiales incorrectos"
description: Aplique el parche ACSD-53628 para corregir el problema de Adobe Commerce en el que el informe CSV de pedidos de venta muestra caracteres especiales incorrectos.
feature: Orders, Data Import/Export
role: Admin, Developer
exl-id: d898fdb8-cab9-49ab-ad8e-43feadf49aa0
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-53628: el informe de pedidos de ventas CSV muestra caracteres especiales incorrectos

El parche ACSD-53628 corrige el problema en el que el informe de pedidos de ventas CSV muestra caracteres especiales incorrectos. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.37 está instalado. El ID del parche es ACSD-53628. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación): 2.4.5-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación): 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El informe CSV de pedidos de venta muestra caracteres especiales incorrectos.

<u>Pasos a seguir</u>:

1. Cambiar **[!UICONTROL Base Currency]** y **[!UICONTROL Default Display Currency]** a Euro en la configuración de moneda.
1. Haga un pedido.
1. En la barra lateral de Administración, vaya a **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Seleccionar fechas. Clic **[!UICONTROL Show Report]**. Clic **[!UICONTROL Export]** para exportar el CSV.

<u>Resultados esperados</u>:

Los caracteres especiales de un archivo CSV exportado se muestran correctamente en Excel.

<u>Resultados reales</u>:

El informe de pedidos de ventas CSV muestra los caracteres especiales incorrectamente.


## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
