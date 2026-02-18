---
title: Problema de token de GitHub y procedimientos de clave del compositor
description: Este artículo proporciona soluciones para el problema de las implementaciones fallidas relacionadas con errores de tokens de Github causados por claves de Compositor obsoletas.
exl-id: 202cb936-f9ba-49ea-bf0a-6e6994d2337a
feature: Identity Management
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Problema de token de GitHub y procedimientos de clave del compositor

Este artículo proporciona soluciones para el problema de las implementaciones fallidas relacionadas con errores de tokens de Github causados por claves de Compositor obsoletas.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, [todas las versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Versiones de Composer 1.10.20 y posteriores

>[!NOTE]
>
>Los comerciantes locales de Adobe Commerce deben consultar con su proveedor de host para asegurarse de que utilizan la versión 1.10.21 o superior del Compositor debido a los cambios de formato de token introducidos por Git.

## Problema

Las implementaciones fallan y los registros de implementación contienen información similar a la siguiente:

*Error grave: Uncatch UnexpectedValueException: El token de oauth de github para github.com contiene caracteres no válidos: &quot;ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx&quot; en /app/vendor/composer/composer/src/Composer/IO/BaseIO.php:129*

## Causa

Las claves de Compositor obsoletas causan errores en el token de Github, lo que provoca implementaciones fallidas.

## Solución

Para resolver el problema, actualice su versión de Composer a la 1.10.22:

1. En su entorno local, ejecute `composer require “composer/composer”:”>1.10.21`.
1. Esto añade el requisito para esa versión del paquete Composer. Compruebe el archivo de bloqueo: la versión `composer/composer` debe ser 1.0.22 o superior.
1. Confirme `composer.json` y `composer.lock` y envíe una implementación.

Si este método no funciona, [envíe un vale de soporte técnico](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket).

## Lectura relacionada

* [Blog de Github: Detrás de los nuevos formatos de token de autenticación de GitHub](https://github.blog/2021-04-05-behind-githubs-new-authentication-token-formats/)
* [Artículo de noticias de InfoQ.com: GitHub cambia el formato de token para mejorar la identificación, la detección de secretos y la entropía](https://www.infoq.com/news/2021/04/github-new-token-format/)
