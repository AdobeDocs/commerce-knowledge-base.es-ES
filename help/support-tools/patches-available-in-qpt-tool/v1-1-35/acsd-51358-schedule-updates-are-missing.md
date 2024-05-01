---
title: "ACSD-51358: Faltan actualizaciones de programación"
description: Aplique el parche ACSD-51358 para corregir el problema de Adobe Commerce en el que los cambios en la actualización programada sin una fecha de finalización llevan a eliminar otras actualizaciones programadas en la misma entidad.
feature: Staging
role: Admin, Developer
exl-id: 8bc4c505-9cf2-4c33-93a1-4b4d7d0dfc15
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51358: faltan actualizaciones programadas

El parche ACSD-51358 corrige el problema en el que los cambios en la actualización programada sin fecha de finalización conducen a eliminar otras actualizaciones programadas en la misma entidad. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 está instalado. El ID del parche es ACSD-51358. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los cambios en la actualización programada sin una fecha de finalización llevan a eliminar otras actualizaciones programadas en la misma entidad.

<u>Pasos a seguir</u>:

1. Crear un **[!UICONTROL scheduled update]** sin la fecha de finalización (*actualización 1*).
1. Crear nuevo **[!UICONTROL scheduled update]** con la misma fecha de inicio que la primera actualización, pero agregue el día siguiente y la fecha de finalización (*actualización 2*).
1. Editar **[!UICONTROL scheduled update]** creado en el paso 1 (*actualización 1*) y los cambios guardados.

<u>Resultados esperados</u>

El (*actualización 2*) debe permanecer en el **[!UICONTROL schedule update]** lista cuando (*actualización 1*) se ha editado.

<u>Resultados reales</u>

El (*actualización 2*) se ha eliminado de **[!UICONTROL schedule update]** lista cuando (*actualización 1*) se ha editado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) en el [!DNL Quality Patches Tool] guía.
