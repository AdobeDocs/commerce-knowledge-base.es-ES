---
title: "MDVA-19640: Los informes avanzados no muestran datos"
description: El parche de MDVA-19640 soluciona el problema cuando los informes avanzados no muestran datos. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. El ID del parche es MDVA-19640. Tenga en cuenta que no hay ningún plan actual para solucionar este problema en versiones futuras.
exl-id: 6df70f10-5d34-4540-b2ae-3a0be32f2bfd
feature: Commerce Intelligence
role: Admin
source-git-commit: 2914a110444898f78d2ed43ea96a9c5f6e70229f
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# MDVA-19640: Los informes avanzados no muestran datos

El parche de MDVA-19640 soluciona el problema cuando los informes avanzados no muestran datos. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 está instalado. El ID del parche es MDVA-19640. Tenga en cuenta que no hay ningún plan actual para solucionar este problema en versiones futuras.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.0

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.1 - 2.4.6-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir</u>:

1. En el Administrador, vaya a **Informes** > **Business Intelligence** y seleccione **Informes avanzados**.
1. Ver el **Informes avanzados** página.

<u>Resultados esperados</u>:

El informe Informes avanzados contiene información, según lo esperado.

<u>Resultados reales</u>:

El informe Informes avanzados no muestra datos.

<u>Pasos adicionales necesarios tras la instalación del parche</u>:

La siguiente consulta SQL debe aplicarse para actualizar registros en la tabla cron_schedule:
`UPDATE core_config_data SET path = REPLACE(path, "crontab/default/jobs/analytics", "crontab/analytics/jobs/analytics") WHERE path LIKE "crontab/default/jobs/analytics%";`

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
