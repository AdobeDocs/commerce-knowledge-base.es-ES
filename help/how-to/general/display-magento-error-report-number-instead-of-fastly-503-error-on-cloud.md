---
title: Mostrar el número de informe de errores de Adobe Commerce en lugar del error Fastly 503
description: 'De forma predeterminada, oculta rápidamente todos los errores de Adobe Commerce detrás del error **503 Servicio no disponible**. Para mostrar el número del informe de registro de errores de Adobe Commerce (para poder encontrarlo en los registros y ver los detalles del error), abra el sitio web omitiendo Fastly siguiendo estos pasos:'
exl-id: c0a4a9f8-a674-4cef-8088-e844594e6076
feature: Cache, Cloud
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%
---
# Mostrar el número de informe de errores de Adobe Commerce en lugar del error Fastly 503

De manera predeterminada, oculta rápidamente todos los errores de Adobe Commerce detrás del error **503 Servicio no disponible**. Para mostrar el número del informe de registro de errores de Adobe Commerce (para poder encontrarlo en los registros y ver los detalles del error), abra el sitio web omitiendo Fastly siguiendo estos pasos:

1. Agregue el dominio y la dirección IP de la aplicación al archivo de hosts del equipo local.
1. Borre la caché y las cookies del explorador (o cambie al modo incógnito).
1. Vuelva a abrir el sitio web de la tienda para ver el error de Adobe Commerce.

Una vez que vea el error de Adobe Commerce auténtico y el número del informe de errores, puede obtener detalles en el archivo del informe de errores siguiendo estos pasos:

1. SSH al entorno afectado. Consulte [SSH a un entorno](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/secure-connections) en nuestra documentación para desarrolladores.
1. Busque el archivo `./var/report/{error_number}`.

## Añadir el dominio de aplicación y la dirección IP al archivo de hosts: pasos detallados

1. Compruebe la IP del servidor del almacén ejecutando el comando `nslookup` en la línea de comandos del equipo local:
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
