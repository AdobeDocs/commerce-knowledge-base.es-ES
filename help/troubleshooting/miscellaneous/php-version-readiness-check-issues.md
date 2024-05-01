---
title: Problemas de comprobación de preparación de versiones de PHP
description: Este artículo habla sobre las soluciones para los problemas de la versión de PHP que podría tener al instalar/actualizar Adobe Commerce en línea mediante el Asistente para configuración web.
exl-id: dee939cf-b9b2-4750-965c-5b8908a4498d
feature: Variables
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# Problemas de comprobación de preparación de versiones de PHP

Este artículo habla sobre las soluciones para los problemas de la versión de PHP que podría tener al instalar/actualizar Adobe Commerce en línea mediante el Asistente para configuración web.

>[!WARNING]
>
>En Adobe Commerce sobre la infraestructura en la nube, tenga en cuenta que las actualizaciones de servicios no se pueden insertar en el entorno de producción sin un aviso de 48 horas laborables a nuestro equipo de infraestructura. Esto es necesario, ya que tenemos que asegurarnos de tener un ingeniero de asistencia técnica de infraestructura disponible para actualizar la configuración dentro de un periodo de tiempo deseado con un tiempo de inactividad mínimo en el entorno de producción. Así que 48 horas antes de cuando sus cambios deben estar en producción [enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) detallando la actualización de servicio necesaria e indicando la hora en la que desea que se inicie el proceso de actualización.

## Productos y versiones afectados

* Adobe Commerce local 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Versión de PHP no compatible

### Problema

La comprobación falla porque está utilizando una versión de PHP no compatible.

### Solución

Para resolver este problema, utilice una de las versiones compatibles que se enumeran en nuestra documentación para desarrolladores [Requisitos del sistema 2.3.x](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements.html) y [Requisitos del sistema 2.2.x](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements.html).

## La comprobación de disponibilidad de PHP no muestra

### Problema

La comprobación de disponibilidad de PHP no muestra la versión de PHP como se muestra en la siguiente figura.
![upgr-shoot-no-cron.png](assets/upgr-tshoot-no-cron.png)

### Solución

Esto es un síntoma de una configuración incorrecta del trabajo cron. Para obtener más información, consulte [Configuración de trabajos cron](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron) en nuestra documentación para desarrolladores.

## Versión de PHP incorrecta

### Problema

La comprobación informa de la versión incorrecta de PHP. Normalmente, esto solo sucede a usuarios avanzados que tienen varias versiones de PHP instaladas. En algunos casos, la comprobación de disponibilidad falla; en otros casos, puede superarse.

Si la versión de PHP reportada por la comprobación de disponibilidad es incorrecta, es el resultado de una discrepancia de versiones de PHP entre la CLI de PHP y el plug-in del servidor web. Adobe Commerce requiere que utilice *una versión* de PHP tanto para la CLI (que ejecuta cron) como para el servidor web (que ejecuta Commerce Admin, Component Manager y System Upgrade).

### Solución

Suponemos que si tienes este problema, eres un usuario avanzado que probablemente ha instalado varias versiones de PHP en tu sistema.

Para resolver el problema, intente lo siguiente:

* Reinicie su servidor web o php-fm.
* Compruebe la `$PATH` para múltiples rutas a PHP.
* Utilice el `which php` para localizar el primer ejecutable de PHP en su ruta; si no es correcto, quítelo o cree un enlace simbólico a la versión de PHP correcta.
* Utilice un [`phpinfo.php`](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/optional.html#install-optional-phpinfo) para recopilar más información.
* Asegúrese de que está ejecutando una versión compatible de PHP de acuerdo con los requisitos de nuestro sistema, en nuestra documentación para desarrolladores:
   * [Requisitos del sistema de Adobe Commerce 2.3.x](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements.html)
   * [Requisitos del sistema para Adobe Commerce 2.2.x](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements.html)
* Establezca la misma configuración de PHP tanto para la línea de comandos de PHP como para el plug-in del servidor web de PHP como se describe en [Opciones de configuración de PHP](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-centos-ubuntu.html) en nuestra documentación para desarrolladores.
