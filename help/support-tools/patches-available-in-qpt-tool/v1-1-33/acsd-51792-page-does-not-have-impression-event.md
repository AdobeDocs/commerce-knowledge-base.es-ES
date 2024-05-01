---
title: "ACSD-51792: La página no tiene evento de impresión"
description: Aplique el parche ACSD-51792 para corregir el problema de rendimiento de Adobe Commerce en el que una página no tiene el evento de impresión cuando Google Tag Manager 4 está habilitado.
exl-id: 59194d4c-c387-4372-a0ff-1cdd74f8c6df
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-51792: La página no tiene evento de impresión

El parche ACSD-51792 corrige el problema de rendimiento en el que una página no tiene el evento de impresión cuando [!DNL Google Tag Manager] 4 está activada. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.33 está instalado. El ID del parche es ACSD-51792. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La página no tiene el evento de impresión cuando [!DNL Google Tag Manager] 4 está activada.

<u>Pasos a seguir</u>:

1. Ir a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**.
1. Configure las variables **[!DNL GoogleTag Manager]** integración.
1. Ir a [Google Tag Assistant](https://tagassistant.google.com/)y complete los pasos necesarios para conectarse al sitio web.
1. Abra una página de categoría que tenga una lista de productos en la tienda.
1. Compruebe el evento de impresiones en el observador del Asistente de etiquetas.

<u>Resultados esperados</u>:

El evento de impresión debe comenzar con todos los productos de la página.

<u>Resultados reales</u>:

La página no tiene el evento de impresión en el observador del Asistente de etiquetas.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
