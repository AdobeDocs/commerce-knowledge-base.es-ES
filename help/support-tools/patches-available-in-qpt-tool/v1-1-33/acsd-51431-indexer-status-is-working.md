---
title: '"ACSD-51431: El estado del indexador es *[!UICONTROL Working]* aunque no haya entradas en el "changelog"'
description: Aplique el parche ACSD-51431 para corregir el problema de Adobe Commerce donde el estado del indexador es *[!UICONTROL Working]* aunque no haya entradas en el registro de cambios.
feature: Logs, Price Indexer
role: Admin
exl-id: 85977b78-7f6b-47c7-b33e-16668bdf98fe
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-51431: el estado del indexador es *[!UICONTROL Working]* aunque no haya entradas en el registro de cambios

El parche ACSD-51431 corrige el problema de rendimiento donde el estado del indexador es *[!UICONTROL Working]* aunque no haya entradas en el registro de cambios. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.33 está instalado. El ID del parche es ACSD-51431. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El estado del indexador es *[!UICONTROL Working]* aunque no haya entradas en el registro de cambios.

<u>Pasos a seguir</u>:

1. Establecer **[!UICONTROL indexers]** hasta [!UICONTROL Update on Schedule].
1. Configure el trabajo cron para que se ejecute cada minuto.
1. Guarde los cambios en diferentes productos simultáneamente.
1. Ejecutar `bin/magento indexer:status` en un par de minutos.

<u>Resultados esperados</u>:

Los cambios se procesan y los indexadores se encuentran en *[!UICONTROL Ready]* estado. El *[!UICONTROL Schedule]* el estado es *[!UICONTROL idle (0 in the backlog)]*.

<u>Resultados reales</u>:

Los cambios se procesan y los indexadores se encuentran en *[!UICONTROL Ready]* estado. Sin embargo, la variable *[!UICONTROL Schedule]* visualizaciones de estado *[!UICONTROL working (0 in the backlog)]*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
