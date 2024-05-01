---
title: .magento.env.yaml no se muestra en env.php después de la implementación
description: Este artículo proporciona una solución al problema en el que los cambios en el archivo .magento.env.yaml no se reflejan en app/etc/env.php después de la implementación.
exl-id: 39ea7295-ba5a-40cc-bc68-a5e0b965c1a7
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# .magento.env.yaml no se muestra en env.php después de la implementación

>[!NOTE]
>
>Si tiene este problema, actualice a ece-tools 2002.1.5 para solucionarlo. 2002.1.5 tiene la funcionalidad de restablecer la opcache en cada implementación, de modo que nunca es necesario cambiar la configuración `opcache.enable_cli=1`. Si no desea actualizar, deberá realizar los pasos de la solución tal como se describe a continuación en la solución.

Este artículo proporciona una solución para el problema en el que los cambios en `.magento.env.yaml` no se reflejan en `app/etc/env.php` después de la implementación.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube (todos [versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)).

## Problema

Cambios realizados en `.magento.env.yaml` no afectan a la variable `app/etc/env.php` generado.

<u>Pasos a seguir:</u>

Cambiar cualquier valor en `.magento.env.yaml` e inserte en el servidor, donde debe definir la configuración (y los ajustes de implementación) del entorno desprotegido actualmente. Para ver los pasos, consulte [Variables de entorno > Implementar variables](https://devdocs.magento.com/cloud/env/variables-deploy.html) en nuestra documentación para desarrolladores.

<u>Resultado esperado:</u>

Cambios realizados en `.magento.env.yaml` afectar al archivo `app/etc/env.php` generado.

<u>Resultado real:</u>

Los cambios no afectan al `app/etc/env.php` después de la implementación.

## Causa

El problema podría deberse al valor incorrecto del `opcache.enable_cli` en el campo `php.ini` archivo.

## Solución

1. Compruebe que el sistema está configurado según lo siguiente [Prácticas recomendadas de rendimiento de Adobe Commerce > Recomendaciones de software](https://devdocs.magento.com/guides/v2.4/performance-best-practices/software.html).
1. Comprobar si `opcache.enable_cli` directiva en `php.ini` se establece en `0` ejecutando: `php -i | grep opcache.enable_cli`
1. Si el resultado es `opcache.enable_cli=1` , edite el `php.ini` en el directorio raíz del proyecto y cambie `opcache.enable_cli=1` hasta `opcache.enable_cli=0`
1. Vuelva a implementar el proyecto.

## Lectura relacionada

* [Cloud for Adobe Commerce > Creación e implementación](https://devdocs.magento.com/cloud/project/magento-env-yaml.html).
