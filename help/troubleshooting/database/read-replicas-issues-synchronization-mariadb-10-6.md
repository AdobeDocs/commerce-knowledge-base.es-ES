---
title: Leer los problemas de Réplicas en Adobe Commerce Cloud 2.4.6 con MariaDB 10.6
description: Este artículo explica cómo solucionar problemas de Leer réplicas en Adobe Commerce Cloud 2.4.6 con MariaDB 10.6.
feature: Configuration
role: Developer,Admin
exl-id: b7af1cc3-93ff-40c5-8959-076cedddb56d
source-git-commit: 724a30310c3841f8280628436925f9a3e5933b14
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Leer los problemas de Réplicas en Adobe Commerce Cloud 2.4.6 con MariaDB 10.6

Este artículo proporciona soluciones para comportamientos inesperados al utilizar Leer réplicas en Adobe Commerce Cloud 2.4.6 con MariaDB 10.6+.

## Productos y versiones afectados

* MariaDB 10.6+
* Adobe Commerce en infraestructura en la nube 2.4.6

## Problema

Las lecturas no críticas muestran información incorrecta.

## Causa

La configuración `slave_parallel_mode` de la base de datos se cambió de forma predeterminada a *optitics* cuando el valor debería ser *conservative* y el valor `synchronous_replication` de Ece-Tools tiene el valor predeterminado *true* cuando el valor debería ser *false*.

## Solución

1. Compruebe que el parámetro `slave_parallel_mode` esté establecido en *conservative* (si el valor no se muestra como [conservative](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=es#submit-ticket), necesitará *elevar un ticket de soporte*). Para comprobarlo, ejecute el siguiente comando:

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

* [Configure variables de entorno para la implementación](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html?lang=es) en la Guía de infraestructura de Commerce en la nube.
* [Prácticas recomendadas para la configuración de bases de datos](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html?lang=es) en el libro de estrategias de implementación.
