---
title: El servidor MySQL ha desaparecido​ error en Adobe Commerce en la nube
description: Este artículo habla sobre la solución del problema en el que recibe un mensaje de error " *SQL server has gone away*" en el archivo "cron.log". Se pueden experimentar una serie de síntomas, incluidos problemas de importación de archivos de imagen o errores de implementación.
exl-id: 14cb9a6d-6d25-4044-8f52-d65648c03431
feature: Cloud, Paas, Services, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '274'
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

1. Compruebe el tiempo de espera actual para `default_socket_timeout` ejecutando en la CLI:    ```    php -i |grep default_socket_timeout    ```
1. Dependiendo del aumento de tiempo de espera establecido, la variable `default_socket_timeout` pasa al tiempo de ejecución más largo esperado posible en el archivo `/etc/platform/<project_name>/php.ini`. Se recomienda configurar entre 10 y 15 minutos.
1. Confírmelo a GIT y vuelva a implementarlo.

## Lectura relacionada

* [Carga de base de datos pierde conexión con MySQL](/help/troubleshooting/database/database-upload-loses-connection-to-mysql.md)
* [Prácticas recomendadas de bases de datos para Adobe Commerce en la infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)
* [Problemas más comunes de la base de datos en Adobe Commerce en la infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html)
