---
title: Leer problemas de réplicas en Adobe Commerce Cloud 2.4.6 con MariaDB 10.6
description: En este artículo se explica cómo solucionar los problemas de las réplicas leídas en Adobe Commerce Cloud 2.4.6 con MariaDB 10.6.
feature: Configuration
role: Developer,Admin
exl-id: b7af1cc3-93ff-40c5-8959-076cedddb56d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# Leer problemas de réplicas en Adobe Commerce Cloud 2.4.6 con MariaDB 10.6

Este artículo proporciona soluciones para comportamientos inesperados al utilizar Leer réplicas en Adobe Commerce Cloud 2.4.6 con MariaDB 10.6+.

## Productos y versiones afectados

* MariaDB 10.6+
* Adobe Commerce en infraestructura en la nube 2.4.6

## Problema

Las lecturas no críticas muestran información incorrecta.

## Causa

La configuración `slave_parallel_mode` de la base de datos se cambió de forma predeterminada a *optitics* cuando el valor debería ser *conservative* y el valor `synchronous_replication` de Ece-Tools tiene el valor predeterminado *true* cuando el valor debería ser *false*.

## Solución

1. Compruebe que el parámetro `slave_parallel_mode` esté establecido en *conservative* (si el valor no se muestra como *conservative*, necesitará [elevar un ticket de soporte](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket)). Para comprobarlo, ejecute el siguiente comando:

   ```
    MariaDB [main]> show variables like 'slave_parallel_mode';
    +---------------------+--------------+
    | Variable_name       | Value        |
    +---------------------+--------------+
    | slave_parallel_mode | conservative |
    +---------------------+--------------+
    1 row in set (0.001 sec)
   ```

1. Actualizar configuraciones de base de datos `.magento.env.yaml` a:

   ```yaml
       DATABASE_CONFIGURATION:
        _merge: true
           slave_connection:
               default:
                   synchronous_replication: false
   ```



Para obtener información sobre cómo actualizar la configuración de la base de datos, consulte [DATABASE_CONFIGURATION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=es#database_configuration) en el tema Implementar variables en la Guía de infraestructura de Commerce en la nube.


## Lectura relacionada

* [Configure variables de entorno para la implementación](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) en la Guía de infraestructura de Commerce en la nube.
* [Prácticas recomendadas para la configuración de bases de datos](/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) en el libro de estrategias de implementación.
