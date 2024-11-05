---
title: Reduzca los "oauth_tokens" caducados antes de la actualización a la versión 2.4.6
description: Este artículo proporciona una solución al problema en el que ve un gran número de oauth_tokens en su tabla oauth_token, lo que puede causar un largo retraso en la actualización a la versión 2.4.6. Se recomienda reducir la tabla "oauth_token" usando CleanExpiredTokens.php.
feature: Variables, Upgrade
role: Developer
exl-id: 92d1d15a-04da-4ba4-b6b8-5c491af9c4c1
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Reducir `oauth_tokens` caducados antes de la actualización a 2.4.6

Este artículo proporciona una solución al problema en el que ve un gran número de `oauth_tokens` en su tabla `oauth_token`, lo que puede causar un largo retraso en la actualización a la versión 2.4.6. Se recomienda reducir la tabla `oauth_token` mediante el trabajo [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] para eliminar los tokens caducados.

## Productos y versiones afectados

* Adobe Commerce 2.4.0 - 2.4.6, todos los métodos de implementación

## Problema

Si hay un gran número de `oauth_tokens` en su tabla `oauth_token`, eso puede causar un largo retraso en la actualización a la versión 2.4.6.

El proceso de actualización incluye el cifrado de esos tokens para obtener una capa adicional de seguridad y solo se realizan 100 registros a la vez. Esto puede tardar varias horas si hay un gran número de tokens.

Si se reduce un gran número de `oauth_tokens` en la tabla `oauth_token`, se puede evitar un largo retraso en la actualización a la versión 2.4.6.

## Solución

Antes de iniciar una actualización, primero asegúrese de que el trabajo [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] se esté ejecutando. Reduce el tamaño de la tabla `oauth_token` al eliminar los tokens de `oauth_tokens` caducados y ya debería estar habilitado de forma predeterminada.

Para almacenar en déclencheur manualmente el trabajo [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron], ejecute:
```bin/magento cron:run --group=default```

## Lectura relacionada

* [Servicios > [!DNL OAuth]](https://experienceleague.adobe.com/docs/commerce-admin/config/services/oauth.html) en la guía de referencia de configuración de Commerce
* [Guía de autenticación](https://developer.adobe.com/developer-console/docs/guides/authentication/) en la guía de Adobe Developer
* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce
