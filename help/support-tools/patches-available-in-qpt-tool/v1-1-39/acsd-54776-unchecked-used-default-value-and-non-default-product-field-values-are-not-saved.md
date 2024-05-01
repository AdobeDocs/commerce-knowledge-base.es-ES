---
title: '''ACSD-54776: desmarcado [!UICONTROL Use Default Value] y los valores de campo de producto no predeterminados no se guardan para el segundo sitio web, tienda y vista de tienda"'
description: Aplique el parche ACSD-54776 para corregir el problema de Adobe Commerce donde la opción no está marcada [!UICONTROL Use Default Value] y los valores de campo de producto no predeterminados no se guardan para la segunda vista del sitio web, la tienda y la tienda.
feature: Products
role: Admin, Developer
exl-id: 5bdad804-8d7b-48b4-ba3b-c2d5387ef55e
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-54776: sin marcar *[!UICONTROL Use Default Value]* y los valores de campo de producto no predeterminados no se guardan

>[!NOTE]
>
>Este parche sustituye al [ACSD-51984](/help/support-tools/patches-available-in-qpt-tool/v1-1-35/acsd-51984-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md) parche lanzado en QPT 1.1.35.

El parche ACSD-54776 corrige el problema en el que la opción sin marcar **[!UICONTROL Use Default Value]** y los valores de campo de producto no predeterminados no se guardan para la segunda vista del sitio web, la tienda y la tienda. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39 está instalado. El ID del parche es ACSD-54776. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.5-p4, 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Desactivado *[!UICONTROL Use Default Value]* y los valores de campo de producto no predeterminados no se guardan para la segunda vista del sitio web, la tienda y la tienda.

<u>Pasos a seguir</u>:

1. Vaya al servidor y navegue hasta **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** y cree un nuevo sitio web, tienda y vista de tienda.
1. Ir a **[!UICONTROL Catalog]** > **[!UICONTROL Products]**, cree un producto simple y guárdelo, y asigne el producto a ambos sitios web desde el **[!UICONTROL Product in Websites]**.
1. Cambie el ámbito a la vista de tienda recién creada en el paso 2.
1. Ir a **[!UICONTROL Search Engine Optimization]** y desmarque **[!UICONTROL Use Default Value]** casillas para [!UICONTROL Meta Title], [!UICONTROL Meta Keywords], y [!UICONTROL Meta Description].
1. Limpie el texto de los campos: *[!UICONTROL Meta Title]*, *[!UICONTROL Meta Keywords]* y *[!UICONTROL Meta Description]* y haga clic en **[!UICONTROL Save]**.
1. Ir a **[!UICONTROL Search Engine Optimization]** otra vez.

<u>Resultados esperados</u>

Se guardan los valores de los campos y las casillas de verificación.

<u>Resultados reales</u>

Los valores de los campos y las casillas de verificación no se guardan.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) en el [!DNL Quality Patches Tool] guía.
