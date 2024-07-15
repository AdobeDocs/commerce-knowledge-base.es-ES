---
title: Sitio en modo de mantenimiento, pero disponible para los clientes
description: Este artículo proporciona una corrección para los casos en los que el modo de mantenimiento está habilitado (un problema de Adobe Commerce en la infraestructura de la nube), pero la tienda sigue estando disponible para los clientes.
exl-id: 61b81fbd-a382-44b5-94e9-5b6d72f11349
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Sitio en modo de mantenimiento, pero disponible para los clientes

Este artículo proporciona una corrección para los casos en los que el modo de mantenimiento está habilitado (un problema de Adobe Commerce en la infraestructura de la nube), pero la tienda sigue estando disponible para los clientes.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube (todas las versiones)

## Problema

<u>Pasos a seguir:</u>

1. Habilite el modo de mantenimiento para el sitio.
1. Vaya a la tienda.

<u>Resultado esperado:</u>

Se muestra la página de mantenimiento.

<u>Resultado real:</u>

Las páginas de la tienda se muestran como de costumbre.

## Causa

Las páginas se siguen almacenando en caché, por lo que la página de mantenimiento no se muestra.

## Solución visible a pesar de estar en modo de mantenimiento

1. SSH a su entorno.
1. Ejecute el comando `php bin/magento cache:clean`.

## Lectura relacionada

[Habilite o deshabilite el modo de mantenimiento](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-maint.html) en nuestra documentación para desarrolladores.
