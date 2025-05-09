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

El parche ACSD-51358 corrige el problema en el que los cambios en la actualización programada sin fecha de finalización conducen a eliminar otras actualizaciones programadas en la misma entidad. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35. El ID del parche es ACSD-51358. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los cambios en la actualización programada sin una fecha de finalización llevan a eliminar otras actualizaciones programadas en la misma entidad.

<u>Pasos a seguir</u>:

1. Crear un **[!UICONTROL scheduled update]** sin la fecha de finalización (*actualización 1*).
1. Crear nuevo(a) **[!UICONTROL scheduled update]** con la misma fecha de inicio que la primera actualización, pero agregar el día siguiente y la fecha de finalización (*actualización 2*).
1. Edite **[!UICONTROL scheduled update]** creado en el paso 1 (*actualizar 1*) y guarde los cambios.

<u>Resultados esperados</u>

La (*actualización 2*) debe permanecer en la lista **[!UICONTROL schedule update]** cuando se edite (*actualización 1*).

<u>Resultados reales</u>

La (*actualización 2*) se quitó de la lista **[!UICONTROL schedule update]** cuando se edita (*actualización 1*).

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es>) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es>) en la guía [!DNL Quality Patches Tool].
