---
title: Eliminar los intentos de inicio de sesión erróneos de la base de datos
description: Este artículo explica cómo eliminar las credenciales de inicio de sesión fallidas preexistentes de la base de datos de Adobe Commerce local y Adobe Commerce en la nube. Para las versiones 2.2.10+ y 2.3.3+, solo necesita ejecutar la secuencia de comandos adjunta. Para las versiones anteriores 2.3.0-2.3.2-p2, debe aplicar un parche para detener el registro y ejecutar el script adjunto para eliminar las credenciales de inicio de sesión fallidas preexistentes.
exl-id: 0d7e3674-3563-414f-86a2-297eb8104099
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# Eliminar los intentos de inicio de sesión erróneos de la base de datos

>[!NOTE]
>
>Este artículo se actualizó el 13 de abril de 2020 con un nuevo script llamado DB\_CLEANUP\_SCRIPT\_v2. Utilice el script DB\_CLEANUP\_SCRIPT\_v2 adjunto para borrar los datos de inicio de sesión erróneos preexistentes en tablas adicionales. Debe utilizar DB\_CLEANUP\_SCRIPT\_v2, incluso si ha ejecutado DB\_CLEANUP\_SCRIPT\_v1 anteriormente para asegurarse de que se limpian las tablas adicionales.

Este artículo explica cómo eliminar las credenciales de inicio de sesión fallidas preexistentes de la base de datos de Adobe Commerce local y Adobe Commerce en la nube. Para las versiones 2.2.10+ y 2.3.3+, solo necesita ejecutar la secuencia de comandos adjunta. Para las versiones anteriores 2.3.0-2.3.2-p2, debe aplicar un parche para detener el registro y ejecutar el script adjunto para eliminar las credenciales de inicio de sesión fallidas preexistentes.

## **Productos y versiones afectados**

* Este problema afecta a Magento Open Source, Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.2.x, 2.3.x y versiones anteriores.
* Las implementaciones de Adobe Commerce 1.x no se ven afectadas.

## Problema

En 2019, se informó a Adobe Commerce de un error que permitía registrar los intentos de inicio de sesión erróneos en una base de datos en Adobe Commerce 2.3.x y 2.2.x. En respuesta, Adobe Commerce incluyó una corrección para este problema en Adobe Commerce 2.3.3 y 2.2.10 (publicado en octubre de 2019). Aunque la corrección de ese error detuvo el registro de intentos de inicio de sesión fallidos, es posible que siga existiendo la información recopilada antes de actualizar a estas versiones actuales. Esta corrección más reciente borra la información de intentos de inicio de sesión que se había registrado anteriormente, si es que la hay.   CVE-2019-8118 se describe y rastrea en [Vulnerabilidades y exposiciones comunes](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-8118).

## Solución

Dependerá de la versión de Adobe Commerce si necesita utilizar el script adjunto y el parche, o solo el script:

**Adobe Commerce y versiones de Magento Open Source 2.3.0-2.3.2-p2**

Para estas versiones, debe aplicar el parche y ejecutar el script de limpieza de la base de datos adjunto para finalizar el registro continuo y eliminar los registros.

1. Ejecute el parche del compositor para detener el registro. Este parche se adjunta al artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo [CLEANUP\_PATCH\_COMPOSER\_2.3.2.patch](assets/CLEANUP_PATCH_COMPOSER_2.3.2.patch.zip). Para obtener instrucciones sobre cómo aplicar el parche, consulte [Cómo aplicar un parche del compositor proporcionado por Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de soporte.

1. Ahora ejecute el script para limpiar la base de datos de los intentos de inicio de sesión fallidos preexistentes. Este script se adjunta al artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo [DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip).

Consulte la [**Cómo ejecutar el script**](/help/troubleshooting/known-issues-patches-attached/remove-failed-login-attempts-from-the-database.md#run_script) para obtener instrucciones.

**Adobe Commerce y versiones de Magento Open Source 2.3.3 y superiores/2.2.10 y superiores**<br>
Solo para estas versiones, ejecute el siguiente script para borrar los registros antiguos (el registro había finalizado anteriormente para estas versiones mediante una corrección publicada en octubre de 2019). Este script se adjunta al artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo [DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip).

Consulte la [**Cómo ejecutar el script**](/help/troubleshooting/known-issues-patches-attached/remove-failed-login-attempts-from-the-database.md#run_script) en nuestra base de conocimiento de soporte, para obtener instrucciones.

**Cómo ejecutar el script**

Siga las siguientes instrucciones para ejecutar el script:

1. Put `DB_CLEANUP_SCRIPT_v2.php` en el directorio raíz de la instalación de Adobe Commerce o Magento Open Source (en el mismo directorio que la aplicación que contiene `app/bootstrap.php`).
1. Ejecute este comando en el terminal: `php DB_CLEANUP_SCRIPT_v2.php` y se iniciará el proceso de limpieza de la base de datos.

Si encuentra algún problema al ejecutar el script, [enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) o envíenos un correo electrónico a [security@magento.com](mailto:security@magento.com).

**Archivos adjuntos**

[CLEANUP\_PATCH\_COMPOSER\_2.3.2.patch](assets/CLEANUP_PATCH_COMPOSER_2.3.2.patch.zip)

[DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip)
