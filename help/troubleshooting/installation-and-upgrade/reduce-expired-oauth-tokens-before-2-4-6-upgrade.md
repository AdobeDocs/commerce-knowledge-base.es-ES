---
title: Reduzca los "oauth_tokens" caducados antes de la actualización a la versión 2.4.6
description: Este artículo proporciona una solución al problema en el que ve un gran número de oauth_tokens en su tabla oauth_token, lo que puede causar un largo retraso en la actualización a la versión 2.4.6. Se recomienda reducir la tabla "oauth_token" usando CleanExpiredTokens.php.
feature: Variables, Upgrade
role: Developer
exl-id: 92d1d15a-04da-4ba4-b6b8-5c491af9c4c1
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# Reducir caducados `oauth_tokens` antes de la actualización a 2.4.6

Este artículo proporciona una solución al problema donde ve un gran número de `oauth_tokens` en su `oauth_token` , lo que puede provocar un gran retraso en la actualización a la versión 2.4.6. Se recomienda reducir el `oauth_token` tabla con el [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] trabajo para eliminar los tokens caducados.

## Productos y versiones afectados

* Adobe Commerce 2.4.0 - 2.4.6, todos los métodos de implementación

## Problema

Si hay un gran número de `oauth_tokens` en su `oauth_token` , esto puede causar un gran retraso en la actualización a la versión 2.4.6.

El proceso de actualización incluye el cifrado de esos tokens para obtener una capa adicional de seguridad y solo se realizan 100 registros a la vez. Esto puede tardar varias horas si hay un gran número de tokens.

Reducción de un gran número de `oauth_tokens` en su `oauth_token` puede evitar un largo retraso en la actualización a la versión 2.4.6.

## Solución

Antes de iniciar una actualización, asegúrese primero de que la variable [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] el trabajo se está ejecutando. Reduce el tamaño del `oauth_token` eliminando la tabla caducada `oauth_tokens` tokens de, y ya deben estar habilitados de forma predeterminada.

Para almacenar en déclencheur manualmente [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] trabajo, ejecutar:
```bin/magento cron:run --group=default```

## Lectura relacionada

* [Servicios > [!DNL OAuth]](https://experienceleague.adobe.com/docs/commerce-admin/config/services/oauth.html) en la Guía de referencia de configuración de Commerce.
* [Guía de autenticación](https://developer.adobe.com/developer-console/docs/guides/authentication/) en la guía de Adobe Developer.
