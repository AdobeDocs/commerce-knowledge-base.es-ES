---
title: "MDVA-39229: Error tras actualizar la hora de inicio de la actualización de ensayo de la regla de catálogo"
description: El parche MDVA-39229 corrige el problema en el que los usuarios reciben un error después de actualizar la hora de inicio de la actualización del ensayo de la regla del catálogo. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5. El ID del parche es MDVA-39229. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: b9a203af-693d-4253-877b-591ae5f388d3
feature: Catalog Management, Staging
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-39229: Error tras actualizar la hora de inicio de la actualización de ensayo de la regla de catálogo

El parche MDVA-39229 corrige el problema en el que los usuarios reciben un error después de actualizar la hora de inicio de la actualización del ensayo de la regla del catálogo. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5. El ID del parche es MDVA-39229. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.4-p2

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios reciben un error después de actualizar la hora de inicio de la actualización de ensayo de la regla de catálogo.

<u>Pasos a seguir</u>:

1. Cree una regla de precio de catálogo.
1. Cree y ejecute cualquier actualización de ensayo.
1. Ejecute la consulta y compruebe que se ha creado el indicador de ensayo.


   `select * from flag;`


1. Cree una nueva actualización de ensayo para que se inicie pasados cinco minutos.
1. Abra **Contenido** > **Ensayo** > **Tablero** > **Nueva actualización** y retrase la hora de inicio en un minuto.
1. Espera seis minutos.
1. Corre cron.

<u>Resultados esperados</u>:

La hora de inicio de la actualización cambia y se aplica la actualización. La actualización anterior se eliminó de la tabla `staging_update`.

<u>Resultados reales</u>:

Los usuarios reciben el siguiente error:

*report.ERROR: el trabajo cron staging_sync_entities_period tiene un error: no se puede eliminar la actualización activa.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
