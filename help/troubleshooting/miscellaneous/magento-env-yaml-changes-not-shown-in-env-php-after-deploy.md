---
title: .magento.env.yaml no se muestra en env.php después de la implementación
description: Este artículo proporciona una solución al problema en el que los cambios en el archivo .magento.env.yaml no se reflejan en app/etc/env.php después de la implementación.
exl-id: 39ea7295-ba5a-40cc-bc68-a5e0b965c1a7
feature: Deploy
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# .magento.env.yaml no se muestra en env.php después de la implementación

>[!NOTE]
>
>Si tiene este problema, actualice a ece-tools 2002.1.5 para solucionarlo. 2002.1.5 tiene funcionalidad para restablecer opcache en cada implementación, de modo que nunca es necesario cambiar la configuración `opcache.enable_cli=1`. Si no desea actualizar, deberá realizar los pasos de la solución tal como se describe a continuación en la solución.

Este artículo proporciona una solución para el problema en el cual los cambios en el archivo `.magento.env.yaml` no se reflejan en `app/etc/env.php` después de la implementación.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura de la nube (todas [las versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)).

## Problema

Los cambios realizados en el archivo `.magento.env.yaml` no afectan al `app/etc/env.php` generado.

<u>Pasos a seguir:</u>

Cambie cualquier valor en `.magento.env.yaml` y envíelo al servidor, donde debería definir la configuración (y las opciones de implementación) para el entorno desprotegido actualmente. Para ver los pasos, consulte [Variables de entorno > Implementar variables](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy) en nuestra documentación para desarrolladores.

<u>Resultado esperado:</u>

Los cambios realizados en el archivo `.magento.env.yaml` afectan al `app/etc/env.php` generado.

<u>Resultado real:</u>

Los cambios no afectan a las variables `app/etc/env.php` después de la implementación.

## Causa

El problema podría deberse al valor incorrecto del parámetro `opcache.enable_cli` en el archivo `php.ini`.

## Solución

1. Compruebe que el sistema esté configurado de acuerdo con [Prácticas recomendadas de rendimiento de Adobe Commerce > Recomendaciones de software](https://experienceleague.adobe.com/es/docs/commerce-operations/performance-best-practices/software).
1. Compruebe si la directiva `opcache.enable_cli` de `php.ini` se ha establecido en `0` al ejecutar: `php -i | grep opcache.enable_cli`
1. Si el resultado es `opcache.enable_cli=1` , edite el archivo `php.ini` en el directorio raíz del proyecto y cambie `opcache.enable_cli=1` a `opcache.enable_cli=0`
1. Vuelva a implementar el proyecto.

## Lectura relacionada

* [Nube para Adobe Commerce > Generar e implementar](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml).
