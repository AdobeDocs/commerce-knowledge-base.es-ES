---
title: La implementación falla con las claves de acceso correctas en env:COMPOSER_AUTH o auth.json
description: Este artículo proporciona una solución para el problema cuando la implementación falla con el siguiente error "No se pudo descargar el archivo https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip (HTTP/1.1 404 No encontrado)".
feature: Deploy
role: Admin
exl-id: a18f4213-7381-4001-a5a0-3f8db4525469
source-git-commit: 7804e7094fb05d1cce9747c8f96c3cfe6bc6171e
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# La implementación falla con las claves de acceso correctas en env:COMPOSER_AUTH o auth.json

Este artículo proporciona una solución para el problema cuando la implementación falla con un error como el que se muestra a continuación, en el [registro de implementación](/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log):

```
W:   [Composer\Downloader\TransportException]
W:   The "https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip" file could not be downloaded (HTTP/1.1 404 Not Found)
```

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube 2.4.x

## Problema

<u>Pasos a seguir</u>:

Intento de implementación.

<u>Resultados esperados</u>:

Se ha implementado correctamente.

<u>Resultados reales</u>:

>[!NOTE]
>
>Este es un error de ejemplo. Podría recibir un error que indique un archivo diferente (según la versión de Adobe Commerce que implemente).

No se ha implementado correctamente. Verá un error como *No se pudo descargar el archivo &quot;https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip&quot; (HTTP/1.1 404 No encontrado)* en el [registro de implementación](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).


### Causa

Es posible que las claves de acceso de compositor especificadas que se encuentran en una de estas ubicaciones no tengan acceso al código:

* en el `env:COMPOSER_AUTH` en el nivel de proyecto
* en el `auth.json file`, que tiene prioridad sobre el `env:COMPOSER_AUTH` variable.

### Solución

Actualice el `env:COMPOSER_AUTH` en el nivel de proyecto y asegúrese de que está configurado con claves que tienen acceso al código.

Para ver los pasos, consulte [Niveles variables](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/variable-levels) en la Guía de Commerce sobre infraestructura en la nube.

## Lectura relacionada

* [No se pudo acceder a Adobe Commerce en el repositorio en la nube: Error 403 prohibido o 404 no encontrado al implementar](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html)
* [Error de implementación: error 7 al descargar... puerto 443: Conexión rechazada](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-error-downloading-connection-refused-adobe-commerce)
