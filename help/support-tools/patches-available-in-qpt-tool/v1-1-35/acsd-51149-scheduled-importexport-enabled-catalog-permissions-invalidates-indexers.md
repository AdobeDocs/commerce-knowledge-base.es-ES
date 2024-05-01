---
title: '''ACSD-51149: Programado [!UICONTROL ImportExport] con habilitado [!UICONTROL Catalog Permissions] invalida los indexadores'
description: Aplique el parche ACSD-51149 para corregir el problema de rendimiento de Adobe Commerce donde el [!UICONTROL ImportExport] con habilitado [!UICONTROL Catalog Permissions] invalida los indizadores.
feature: Cache, Data Import/Export
role: Admin
exl-id: 3a26f4be-8e52-407d-bb25-2841458f3aa5
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-51149: programado [!UICONTROL ImportExport] con habilitado [!UICONTROL Catalog Permissions] invalida los indexadores

El parche ACSD-51149 corrige el problema en el que el [!UICONTROL ImportExport] con habilitado [!UICONTROL Catalog Permissions] invalida los indizadores. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.35 está instalado. El ID del parche es ACSD-51149. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Programado [!UICONTROL ImportExport] con habilitado [!UICONTROL Catalog Permissions] invalida los indizadores.

<u>Pasos a seguir</u>:

1. Activar *[!UICONTROL Catalog Permissions]*.
1. Establezca todos los indexadores en *[!UICONTROL Update by Schedule]*.
1. Cree un producto sencillo.
1. Exportar este producto mediante **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]**.
1. Descargue el CSV exportado y colóquelo en `<AC root folder>/var/import`.
1. Cree una importación de producto programada con el CSV descargado.
1. Ejecutar reindexación completa.
1. Compruebe el estado de los indexadores. Todos los indexadores deben estar en *[!UICONTROL Ready]* estado.
1. Ejecute la importación programada creada desde la cuadrícula.
1. Vuelva a comprobar el estado de los indexadores.

<u>Resultados esperados</u>:

Todos los indexadores están en la *[!UICONTROL Ready]* estado.

<u>Resultados reales</u>:

Algunos de los indexadores están en *[!UICONTROL Reindex Required]* estado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
