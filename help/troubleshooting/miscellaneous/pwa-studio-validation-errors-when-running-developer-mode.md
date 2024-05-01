---
title: "PWA Studio: Errores de validación al ejecutar el modo de desarrollador"
description: En este tema se describe una solución para los casos en los que se producen errores de validación al ejecutar el modo de desarrollador en Progressive Web App (PWA) Studio for Adobe Commerce como resultado de no haber creado anteriormente el concepto de venia (Venia es una tienda PWA). archivo de entorno. Este archivo contendrá las variables para su entorno de desarrollo local.
exl-id: 97d042ef-88e6-4eda-a834-2cff4de276e2
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# PWA Studio: Errores de validación al ejecutar el modo de desarrollador

En este tema se describe una solución para los casos en los que se producen errores de validación al ejecutar el modo de desarrollador en Progressive Web App (PWA) Studio for Adobe Commerce como resultado de no haber creado anteriormente el concepto de venia (Venia es una tienda PWA). archivo de entorno. Este archivo contendrá las variables para su entorno de desarrollo local.

## Productos y versiones afectados

* PWA Studio para Adobe Commerce

## Problema

<u>Paso para reproducir</u>:

* Ejecute el modo de desarrollador en PWA Studio para Adobe Commerce.

<u>Resultado esperado</u>:

* El servidor de PWA Studio se inicia normalmente.

<u>Resultado real</u>:

* Verá errores de validación que pueden ser similares a:

```
    ⓧ  Missing required environment variables:         MAGENTO_BACKEND_URL: Connect to an instance of Adobe Commerce 2.3 by specifying its public domain name. (eg.         "https://master-7rqtwti-mfwmkrjfqvbjk.us-4.magentosite.cloud/")      ⚠  No .env file in ./packages/venia-concept. Autogenerate a .env file by running the command 'buildpack         create-env-file ./packages/venia-concept'.
```

## Causa

Falta el archivo de variables de entorno para el entorno de desarrollo local. El archivo que genera el siguiente comando contendrá las variables para su entorno de desarrollo local.

## Solución

Asegúrese de ejecutar el comando

```
npx @magento/pwa-buildpack create-env-file packages/venia-concept
```

en el directorio raíz para generar el archivo que contendrá las variables para su entorno de desarrollo local.

## Lectura relacionada

* [PWA Studio para la documentación de Adobe Commerce](https://magento.github.io/pwa-studio/)
* [Tienda Venia (Concepto)](https://magento.github.io/pwa-studio/venia-pwa-concept/)
