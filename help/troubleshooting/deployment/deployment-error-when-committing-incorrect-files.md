---
title: Errores de implementación al confirmar archivos incorrectos
description: Este artículo proporciona una solución para el problema que se produce cuando se producen errores de implementación causados por confirmaciones incorrectas en el repositorio de archivos/carpetas que no deberían haberse agregado.
feature: Deploy
role: Developer
exl-id: c795f9d5-7171-4846-b99f-c018f1d2bf12
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '159'
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
