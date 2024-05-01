---
title: '"ACSD-54319: El precio del producto muestra cero en *[!UICONTROL Products in Carts]* informe'''
description: Aplique el parche ACSD-54319 para corregir el problema de Adobe Commerce en el que el precio del producto muestra cero en *[!UICONTROL Products in Carts]* informe
feature: Reporting, Products
role: Admin, Developer
exl-id: f53b3ed3-d5d5-461c-bba2-4f9f3f038580
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# ACSD-54319: el precio del producto muestra cero en *[!UICONTROL Products in Carts]* informe

El parche ACSD-54319 corrige el problema en el que el precio del producto es cero en *[!UICONTROL Products in Carts]* informe. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 está instalado. El ID del parche es ACSD-54319. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.5-p5

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El precio del producto es cero en *[!UICONTROL Products in Carts]* informe.

<u>Pasos a seguir</u>:

1. Establecer **[!UICONTROL Catalog Price Scope]** hasta **[!UICONTROL Website]** de **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]**.
1. Creación de un segundo sitio web desde **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**.
1. Crear un producto desde **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Asigne este producto únicamente al segundo sitio web.
1. Añada un producto al carro de compras desde el segundo sitio web.
1. Ir a **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Marketing]** > **[!UICONTROL Products In Carts]** rejilla.
1. Compruebe la *[!UICONTROL Price]* columna en *[!UICONTROL Products In Carts]* rejilla.

<u>Resultados esperados</u>:

El precio del producto no es cero en *[!UICONTROL Products in Carts]* cuadrícula del informe.

<u>Resultados reales</u>:

El precio del producto es cero en *[!UICONTROL Products in Carts]* cuadrícula del informe.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
