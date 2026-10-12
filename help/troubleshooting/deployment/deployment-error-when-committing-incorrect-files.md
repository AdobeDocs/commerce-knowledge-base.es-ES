---
title: Errores de implementación al confirmar archivos incorrectos
description: Este artículo proporciona una solución para el problema que se produce cuando se producen errores de implementación causados por confirmaciones incorrectas en el repositorio de archivos/carpetas que no deberían haberse agregado.
feature: Deploy
role: Developer
exl-id: c795f9d5-7171-4846-b99f-c018f1d2bf12
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%
---
# Errores de implementación al confirmar archivos incorrectos

Este artículo proporciona una corrección del problema cuando se obtienen errores de implementación causados por confirmaciones incorrectas en el repositorio de archivos/carpetas que no deberían haberse agregado.

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube (todas las versiones)

## Problema

Se están obteniendo errores de implementación al confirmar en el repositorio de archivos/carpetas. Por ejemplo, el siguiente error se debe a un intento de conexión a la base de datos cuando no está disponible actualmente durante la [fase de compilación](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#build-phase):

```SQL
SQLSTATE[HY000] [2002] php_network_getaddresses: getaddrinfo for database.i  
          nternal failed: Name or service not known                                    
                                                                                       
        
        In Abstract.php line 124:
                                                                                       
          SQLSTATE[HY000] [2002] php_network_getaddresses: getaddrinfo for database.i  
          nternal failed: Name or service not known                                    
                                                                                       
        
        In Abstract.php line 124:
                                                                                       
          PDO::__construct(): php_network_getaddresses: getaddrinfo for database.inte  
          rnal failed: Name or service not known       
```

## Causa

Ciertos archivos o carpetas no deben enviarse al repositorio, ya que podrían interrumpir el [flujo de trabajo de implementación](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html).

## Solución

Elimine estos archivos o carpetas del repositorio si están presentes:

* `app/etc/env.php`
* `pub/media/catalog`
* `vendor`
