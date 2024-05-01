---
title: Mostrar el número de informe de errores de Adobe Commerce en lugar del error Fastly 503
description: '"De forma predeterminada, Fastly oculta todos los errores de Adobe Commerce detrás del error Servicio no disponible **503**. Para mostrar el número del informe de registro de errores de Adobe Commerce (para poder encontrarlo en los registros y ver los detalles del error), abra el sitio web omitiendo Fastly siguiendo estos pasos:'''
exl-id: c0a4a9f8-a674-4cef-8088-e844594e6076
feature: Cache, Cloud
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Mostrar el número de informe de errores de Adobe Commerce en lugar del error Fastly 503

De forma predeterminada, oculta rápidamente todos los errores de Adobe Commerce detrás de **Servicio 503 no disponible** error. Para mostrar el número del informe de registro de errores de Adobe Commerce (para poder encontrarlo en los registros y ver los detalles del error), abra el sitio web omitiendo Fastly siguiendo estos pasos:

1. Agregue el dominio y la dirección IP de la aplicación al archivo de hosts del equipo local.
1. Borre la caché y las cookies del explorador (o cambie al modo incógnito).
1. Vuelva a abrir el sitio web de la tienda para ver el error de Adobe Commerce.

Una vez que vea el error de Adobe Commerce auténtico y el número del informe de errores, puede obtener detalles en el archivo del informe de errores siguiendo estos pasos:

1. SSH al entorno afectado. Consulte [SSH a un entorno](https://devdocs.magento.com/guides/v2.3/cloud/env/environments-ssh.html#ssh) en nuestra documentación para desarrolladores.
1. Busque el `./var/report/{error_number}` archivo.

## Añadir el dominio de aplicación y la dirección IP al archivo de hosts: pasos detallados

1. Compruebe la IP del servidor de su tienda ejecutando `nslookup` en la línea de comandos del equipo local:
   * Usuarios de arquitectura profesional (entornos de ensayo y producción):

   ```
   nslookup {your_project_id}.ent.magento.cloud
   ```

   * Usuarios de arquitectura inicial (todos los entornos); usuarios de arquitectura Pro (entorno de integración):

   ```
   nslookup gw.{your_region}.magentosite.cloud
   ```

1. Añada el dominio de almacén y la IP del servidor de aplicaciones al archivo de hosts de su equipo local con el siguiente formato:

```
{server_IP} {store_domain}
```
