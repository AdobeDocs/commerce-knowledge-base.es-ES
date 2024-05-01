---
title: "Parche de MDVA-28409: error del servidor web de Adobe Commerce: memoria insuficiente"
description: El parche MDVA-28409 resuelve el problema en el que el trabajo cron para eliminar ofertas se detuvo debido a la necesidad de procesar un gran número de elementos. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.5.
exl-id: 175e5f2f-2f76-42ee-83e9-c1b23ff81e96
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Parche de MDVA-28409: error en el servidor web de Adobe Commerce: memoria insuficiente

El parche MDVA-28409 resuelve el problema en el que el trabajo cron para eliminar ofertas se detuvo debido a la necesidad de procesar un gran número de elementos. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.5 está instalado.

## Productos y versiones afectados

Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.4 - 2.3.5, 2.4.0

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El problema es que el trabajo cron se ha quedado sin memoria debido a la cantidad de datos que el trabajo está intentando procesar. Los síntomas de este problema incluyen bajo rendimiento debido al alto uso de disco por parte de MySQL y baja memoria del servidor web.

<u>Pasos a seguir:</u>

Para comprobar si hay un trabajo cron que no pueda eliminar las comillas obsoletas, ejecute la siguiente consulta:

```
select * from cron_schedule where job_code like '%sales_clean_quotes%'
```

<u>Resultado esperado:</u>

El estado de `sales_clean_quotes` el trabajo cron debe ser `success`.

<u>Resultado real:</u>

El estado de `sales_clean_quotes` el trabajo cron es `running` o `error`.

Otra forma de confirmar que hay un trabajo cron que no puede eliminar comillas obsoletas es asignar el resultado de la consulta desde **Paso 1** (`executed_at`) con las marcas de tiempo de cualquier error de memoria en `/var/log/cron.log`. Si hay un trabajo cron que no puede procesar la cantidad de datos, puede ver un mensaje similar al siguiente:

```
PHP Fatal error:  Allowed memory size of 1073741824 bytes exhausted (tried to allocate 4096 bytes) in /app/vendor/magento/framework/DB/Statement/Pdo/Mysql.php on line 91

Fatal error: Allowed memory size of 1073741824 bytes exhausted (tried to allocate 4096 bytes) in /app/vendor/magento/framework/DB/Statement/Pdo/Mysql.php on line 91
--
[2020-05-30 05:00:27.224718] Launching command 'php bin/magento cron:run'.
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sección.
