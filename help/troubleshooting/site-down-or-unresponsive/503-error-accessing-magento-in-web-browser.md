---
title: Error 503 al acceder a Adobe Commerce en el explorador web
description: Este artículo proporciona una posible solución al problema en el que se produce un error 503 al intentar acceder a la tienda o el administrador de Adobe Commerce.
exl-id: 4232aa21-40c2-41b0-9fb0-fc8cd4db8e39
feature: Storefront
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# Error 503 al acceder a Adobe Commerce en el explorador web

Este artículo proporciona una posible solución al problema en el que se produce un error 503 al intentar acceder a la tienda o el administrador de Adobe Commerce.

## Productos y versiones afectados

Adobe Commerce 2.3.x

## Problema {#symptoms}

<u>Pasos a seguir</u>

(Requisitos previos: asegúrese de que la tienda no esté en [modo de mantenimiento](https://experienceleague.adobe.com/es/docs/commerce-operations/configuration-guide/cli/set-mode#config-mode-show)).

Vaya al administrador de Commerce o a la tienda en un navegador web.

<u>Resultado esperado</u>

Se carga la página.

<u>Resultado real</u>

Recibe el error HTTP 503 (Servicio no disponible). Apache `error.log` incluye el siguiente mensaje:

*El comando &#39;Order&#39; no es válido, quizás esté mal escrito o definido por un módulo no incluido en la configuración del servidor.*

## Causa {#details}

El módulo de compatibilidad de Apache 2.4 `mod_access_compat` está deshabilitado, lo que hace que las reescrituras de URL de Adobe Commerce no funcionen correctamente.

## Solución {#suggested-solution}

Habilite el módulo Apache `mod_access_compat` y reinicie Apache ejecutando el siguiente comando como usuario con privilegios &quot;root&quot;:

```bash
a2enmod access_compat
service <name> restart
```

En CentOS,

```bash
<name>
```

es

```bash
httpd
```

. En Ubuntu,

```bash
<name>
```

es

```bash
apache2
```

.

## Lectura relacionada {#additional-resources}

* [Documentación de Apache sobre mod\_access\_compat](https://httpd.apache.org/docs/current/mod/mod_access_compat.html)
* [Documentación de Apache sobre mod\_authz\_host](https://httpd.apache.org/docs/current/mod/mod_authz_host.html)
* [Pedir, permitir, denegar desde la guía de Apache Definitive](https://docstore.mik.ua/orelly/linux/apache/ch05_06.htm)
* [askubuntu.com](https://askubuntu.com/questions/335228/changes-in-apache-config-between-12-04-2-and-12-04-3-lts)
