---
title: 'ACSD-51294: precio, cantidad, impuestos, envío, ingresos enviados como cadena a [!DNL Google Analytics] y GTM'
description: Aplique el parche ACSD-51294 para solucionar el problema de Adobe Commerce, donde el precio, la cantidad, los impuestos, el envío y los ingresos se envían como una cadena a [!DNL Google Analytics] y GTM.
feature: Orders, Shipping/Delivery, Variables
role: Admin
exl-id: 159e1e98-0def-4b20-901d-f5f58c3ead7c
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51294: precio, cantidad, impuesto, envío, ingresos enviados como cadena a [!DNL Google Analytics] y GTM

El parche ACSD-51294 corrige el problema por el que el precio, la cantidad, los impuestos, el envío y los ingresos se envían como una cadena a [!DNL Google Analytics] y GTM. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.32 está instalado. El ID del parche es ACSD-51294. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El precio, la cantidad, los impuestos, el envío y los ingresos se envían como una cadena a [!DNL Google Analytics] y GTM.

<u>Pasos a seguir</u>:

1. Configurar [!DNL Google Tag Manager] navegando a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]** > **[!UICONTROL Google GTag]** > **[!UICONTROL Google Analytics4]**.
2. Cree un producto sencillo.
3. Complete el cierre de compra con ese producto.
4. Compruebe la `dataLayer` Variable JavaScript en la página de cierre de compra correcta.

<u>Resultados esperados</u>

Los valores de precio y cantidad son numéricos.

<u>Resultados reales</u>

Los valores de precio y cantidad son de cadena.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) en el [!DNL Quality Patches Tool] guía.
