---
title: Sitio en modo de mantenimiento, pero disponible para los clientes
description: Este artículo proporciona una corrección para los casos en los que el modo de mantenimiento está habilitado (un problema de Adobe Commerce en la infraestructura de la nube), pero la tienda sigue estando disponible para los clientes.
exl-id: 61b81fbd-a382-44b5-94e9-5b6d72f11349
feature: Cache
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '159'
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

[Habilite o deshabilite el modo de mantenimiento](https://experienceleague.adobe.com/es/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) en nuestra documentación para desarrolladores.
