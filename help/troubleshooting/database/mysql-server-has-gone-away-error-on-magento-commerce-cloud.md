---
title: El servidor MySQL ha desaparecido​ error en Adobe Commerce en la nube
description: Este artículo habla sobre la solución del problema en el que recibe un mensaje de error " *SQL server has gone away*" en el archivo "cron.log". Se pueden experimentar una serie de síntomas, incluidos problemas de importación de archivos de imagen o errores de implementación.
exl-id: 14cb9a6d-6d25-4044-8f52-d65648c03431
feature: Cloud, Paas, Services, Variables
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
subfeature_v2:
  - id: 2191e157-828a-5358-ad69-ebcaa8402915
    internal-label: Variables
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%
---
# El servidor MySQL ha desaparecido&#x200B; error en Adobe Commerce en la nube

Este artículo trata sobre la solución del problema en el que recibe un mensaje de error &quot;*SQL server has gone away*&quot; en el archivo `cron.log`. Se pueden experimentar una serie de síntomas, incluidos problemas de importación de archivos de imagen o errores de implementación.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, todas [versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problema

Recibirá un mensaje de error &quot;*SQL server has gone away*&quot; en el archivo `cron.log`.

<u>Pasos a seguir</u>

Importar archivos y almacenar en déclencheur una implementación.

<u>Resultado esperado</u>

Implementación correcta.

<u>Resultado real</u>

Mensaje de error en `cron.log` :&quot; *SQLSTATE\[HY000\] \[2006\] El servidor MySQL ha desaparecido at/app/AAAAAAAAA/vendor/magento/zendframework1/library/Zend/Db/Adapter/Pdo/Abstract.php:144&quot;*

## Causa

El valor `default_socket_timeout` se ha establecido demasiado bajo. Esto se debe a la configuración `default_socket_timeout` Si php no recibe nada de la base de datos MySQL dentro de este período, supone que está desconectado y arroja el error.

## Solución

1. Compruebe el tiempo de espera actual para `default_socket_timeout` ejecutando la CLI: `php -i |grep default_socket_timeout`.
1. Compruebe el tiempo de espera actual para `default_socket_timeout` ejecutando en la CLI: `php -i |grep default_socket_timeout`
1. Dependiendo del aumento de tiempo de espera establecido, la variable `default_socket_timeout` pasa al tiempo de ejecución más largo esperado posible en el archivo `/etc/platform/<project_name>/php.ini`. Se recomienda configurar entre 10 y 15 minutos.
1. Confírmelo a GIT y vuelva a implementarlo.

## Lectura relacionada

* [Prácticas recomendadas de bases de datos para Adobe Commerce en infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)
* [Problemas más comunes de las bases de datos en Adobe Commerce sobre la infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html)
