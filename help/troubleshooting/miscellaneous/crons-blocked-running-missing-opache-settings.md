---
title: Cron se detiene debido a que falta  [!DNL OpCache] configuración o está mal configurado
description: Este artículo proporciona una solución cuando los crons dejan de funcionar debido a que faltan  [!DNL OpCache] configuraciones o están mal configuradas.
exl-id: 30643ea9-969f-41c8-8e62-b24e56d690cf
feature: Cache
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Cron se detuvo debido a una configuración incorrecta o a la falta de la configuración de [!DNL OpCache]

Este artículo proporciona una solución para los casos en los que cron deja de funcionar debido a la falta de la configuración de [!DNL OpCache] o a que esta no está configurada correctamente.

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube, [todas las versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problema

El cron dejó de funcionar.

## Causa

El módulo [!DNL OpCache] se actualizó a una versión más reciente que introdujo un complemento [!DNL GraphQL] que reescribe `env.php` en tiempo de ejecución y podría anular la configuración de cron, lo que puede haber causado el problema. La configuración de [!DNL OpCache] debe actualizarse para evitar problemas con `env.php file`, y eso se resolvió en la [versión 2002.1.13](/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package.html?lang=en#v2002.1.13) del paquete [!DNL ECE Tools].

## Solución

Opción 1: ejecute lo siguiente en la herramienta de línea de comandos:

```bash
bin/magento cron:run
```

Un mensaje puede mostrar que el cron está deshabilitado.

Opción 2: abrir el archivo `app/etc/env.php`: si ve lo siguiente, la cron se deshabilitó manualmente, no se volvió a habilitar debido a un error en la implementación o el problema estaba relacionado con la configuración de [!DNL OpCache].

```php
  'cron' =>
  array (
    'enabled' => 0,
  ),
```

1. Si el cron está deshabilitado, ejecute este comando para volver a habilitar el cron: `vendor/bin/ece-tools cron:enable`
1. Asegúrese de que se encuentra en la última versión de [!DNL ECE Tools]. Si no lo está, actualice (o salte al elemento 3). Para comprobar la versión existente, ejecute este comando:
   `composer show magento/ece-tools`
1. Si ya se encuentra en la última versión de [!DNL ECE Tools], compruebe la presencia del archivo `op-exclude.txt`. Para ello, ejecute este comando:
   `ls op-exclude.txt`.
Si este archivo no está presente, agregue https://github.com/magento/magento-cloud/blob/master/op-exclude.txt a su repositorio, confirme el cambio y vuelva a implementar.
1. Sin tener que actualizar [!DNL ECE Tools], también puede agregar o modificar https://github.com/magento/magento-cloud/blob/master/op-exclude.txt en su repositorio, confirmar el cambio y volver a implementar.

## Lectura relacionada

* [Problemas de comprobación de preparación de Cron](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues.html)
* [Propiedad Crons](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html)
* [El trabajo de cron está atascado en el estado &quot;en ejecución&quot;](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html)
