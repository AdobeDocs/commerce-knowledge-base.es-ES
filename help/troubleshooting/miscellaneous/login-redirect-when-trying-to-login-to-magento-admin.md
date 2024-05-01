---
title: Redirección de inicio de sesión al intentar iniciar sesión en el administrador de Commerce
description: Este artículo ofrece las posibles soluciones para el problema de inicio de sesión del administrador de Commerce, por el que se le redirige de nuevo al formulario de inicio de sesión al intentar iniciar sesión en el administrador y no se muestra ningún mensaje de error. Esto incluye corregir la configuración de zona horaria del servidor y borrar la configuración de cookies en Adobe Commerce.
exl-id: ff3114fd-8690-4983-8221-cf807f083b15
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Redirección de inicio de sesión al intentar iniciar sesión en el administrador de Commerce

Este artículo ofrece las posibles soluciones para el problema de inicio de sesión del administrador de Commerce, por el que se le redirige de nuevo al formulario de inicio de sesión al intentar iniciar sesión en el administrador y no se muestra ningún mensaje de error. Esto incluye corregir la configuración de zona horaria del servidor y borrar la configuración de cookies en Adobe Commerce.

## Ediciones y versiones afectadas:

Todas las versiones y ediciones de Adobe Commerce.

## Problema

<u>Pasos a seguir</u>:

1. Vaya a la página de administración de Commerce.
1. Introduzca sus credenciales de y haga clic en Iniciar sesión.

<u>Resultados esperados</u>:

Ha iniciado sesión en el administrador de Commerce.

<u>Resultados reales</u>:

Se le redirigirá al formulario de inicio de sesión sin mensajes de error.

## Causa

Hay un par de razones posibles para el problema:

* Zona horaria incorrecta establecida en el nivel del explorador (lo que hace que la sesión de administrador se considere caducada aunque su duración real aún no haya caducado).
* Configuración de cookies incorrecta, lo que hace que la sesión establecida no sea utilizada por Adobe Commerce.

Consulte los párrafos siguientes para ver las soluciones en cada caso.

## Soluciones

### Problema de duración de sesión de administrador

Intente utilizar un explorador diferente y aumente la duración de la sesión de administración si es inferior a una hora.

Para aumentar la duración de la sesión de administración, siga estos pasos:

1. Cree una copia de seguridad de base de datos.
1. Utilice una herramienta de base de datos como [phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin), o acceda a la base de datos manualmente desde la línea de comandos para ejecutar la siguiente consulta SQL:

   ```sql
   UPDATE core_config_data SET value = 7200 WHERE path = 'admin/security/session_lifetime';
   ```

1. Limpie la caché de configuración ejecutando el siguiente comando:

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

### Configuración de cookies incorrecta

Para comprobar los valores de configuración de las cookies y borrarlos, siga estos pasos:

1. Cree una copia de seguridad de base de datos.
1. Utilice una herramienta de base de datos como [phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin), o acceda a la base de datos manualmente desde la línea de comandos para ejecutar la siguiente consulta SQL:

   ```sql
   SELECT * FROM core_config_data WHERE (path = "web/cookie/cookie_domain" OR path = "web/cookie/cookie_path");
   ```

1. Si las respuestas de los valores no están vacías, establézcalas en NULL ejecutando:

   ```sql
   UPDATE core_config_data SET value = NULL WHERE (path = "web/cookie/cookie_domain" OR path = "web/cookie/cookie_path");
   ```

1. Limpie la caché de configuración ejecutando el siguiente comando:

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

## Artículos relacionados

* [Vuelva al formulario de inicio de sesión de administrador con el error &quot;Su cuenta está temporalmente desactivada&quot;.](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error.md) en nuestra base de conocimiento de soporte.
* [Volver a redirigir al formulario de inicio de sesión de administrador con el error &quot;La sesión actual ha caducado&quot;](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-current-session-has-been-expired-error.md) en nuestra base de conocimiento de soporte.
