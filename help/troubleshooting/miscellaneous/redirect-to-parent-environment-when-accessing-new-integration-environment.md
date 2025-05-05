---
title: Redirigir al entorno principal al acceder al nuevo entorno de integración
description: Este artículo proporciona instrucciones para la resolución de problemas del problema de infraestructura en la nube de Adobe Commerce, donde al intentar acceder al entorno de integración recién creado, se le redirige al entorno principal.
exl-id: d1d40c8d-d43c-442e-95c9-76f3cdcafb0e
feature: Cache, Integration, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Redirigir al entorno principal al acceder al nuevo entorno de integración

Este artículo proporciona instrucciones para la resolución de problemas del problema de infraestructura en la nube de Adobe Commerce, donde al intentar acceder al entorno de integración recién creado, se le redirige al entorno principal.

Para solucionarlo, debe corregir el valor base\_url en la base de datos y asegurarse de que el valor de la variable `UPDATE_URLS` está establecido en `true`. Encuentre más detalles en las secciones a continuación.

Versiones y ediciones afectadas:

* Adobe Commerce en infraestructura en la nube 2.X.X

## Problema

<u>Pasos a seguir</u>:

1. Clone la rama de integración existente.
1. Haga clic en la URL para acceder al nuevo entorno.

<u>Resultado esperado</u>:

Se llega al entorno recién creado.

<u>Resultado real</u>:

Se le redirigirá al entorno en la rama principal.

## Solución

Para solucionar el problema, debe corregir los valores de `base_url` (seguros y no seguros) en la base de datos de entorno personalizada y establecer la variable `UPDATE_URL` en el archivo `.magento.env.yaml`.

### Valores base\_url correctos en la base de datos

Los cambios en la base de datos se pueden realizar manualmente o mediante la CLI de Adobe Commerce, en caso de que se encuentre en la versión 2.2.0 o posterior.

#### Corrija los valores en la base de datos manualmente

1. Conéctese a la base de datos.
1. Ejecute los siguientes comandos:

```sql
UPDATE core_config_data SET value = %your_new_environment_unsecure_url% WHERE path="web/unsecure/base_url"
```

```sql
update core_config_data set value = %your_new_environment_secure_url% where path="web/secure/base_url"
```

#### Corrija la base de datos utilizando Adobe Commerce CLI (disponible para las versiones 2.2.X)

1. Inicie sesión como propietario del [sistema de archivos Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/web-server/apache.html?lang=es) o cambie a él.
1. Ejecute los siguientes comandos:

```bash
php <your_magento_install_dir>/bin/magento config:set web/unsecure/base_url http://example.com
php <your_magento_install_dir>/bin/magento config:set web/secure/base_url https://example.com
```

### Establecer la variable `UPDATE_URLS`

En la base de código local, en el conjunto de archivos `.magento.env.yaml`:

```
 stage:
    deploy:
        UPDATE_URLS: true
```

### Borrar caché de configuración

Para que se apliquen los cambios, limpie la caché de configuración ejecutando el siguiente comando:

```bash
php <your_magento_install_dir>/bin/magento cache:clean config
```

## Artículo relacionado en nuestra documentación para desarrolladores:

[Implementar variables](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=es)
