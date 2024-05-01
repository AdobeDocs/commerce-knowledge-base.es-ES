---
title: Las páginas de cierre de compra no se cargan cuando el bloqueador de anuncios está habilitado
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce en la infraestructura en la nube 2.2.2 relacionado con el error al cargar las páginas de cierre de compra causado por uBlock u otros bloqueadores de anuncios.
exl-id: fe718f21-df23-4ab1-a6b0-03bad4d7095d
feature: Checkout, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# Las páginas de cierre de compra no se cargan cuando el bloqueador de anuncios está habilitado

Este artículo proporciona un parche para el problema conocido de Adobe Commerce en la infraestructura en la nube 2.2.2 relacionado con el error al cargar las páginas de cierre de compra causado por uBlock u otros bloqueadores de anuncios.

## Problema

Si Google Analytics está habilitado para la tienda, cuando un cliente con uBlock u otro bloqueador de anuncios instalado continúa con el cierre de compra, la variable `trackingCode.js` Se ha bloqueado la carga del archivo y RequireJS interrumpe el flujo de ejecución de JS. Esto causa problemas al cargar la página de cierre de compra.

<u>Pasos a seguir</u> :

Requisitos previos: Un bloqueador de anuncios debe estar instalado y activo en el explorador.

1. En el Administrador de Commerce, habilite y configure la funcionalidad Google Analytics.
1. Abra una página de producto en la tienda.
1. Añadir productos al carro de compras.
1. Haga clic en **Ir a Cierre de compra** vínculo.

<u>Resultado esperado</u>: la página de cierre de compra se carga y el cliente puede completar el cierre de compra.

<u>Resultado real</u>: la página de cierre de compra no se carga; el indicador de carga nunca desaparece.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[Descargar MDVA-9353\_EE\_2.2.2\_v1.composer.patch](assets/MDVA-9353_EE_2.2.2_v1.composer.patch.zip)

### Versiones de Adobe Commerce compatibles:

El parche se ha creado para:

* Adobe Commerce en la infraestructura en la nube 2.2.2

El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce en la infraestructura en la nube de 2.1.0 a 2.1.14
* Adobe Commerce en la infraestructura en la nube de 2.2.0 a 2.2.1 y de 2.2.3 a 2.2.5
* Adobe Commerce local de 2.1.0 a 2.1.14
* Adobe Commerce local de 2.2.0 a 2.2.5

## Cómo aplicar el parche

Para obtener instrucciones, consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de soporte.

## Vínculos útiles

* [El problema tratado en GitHub](https://github.com/magento/magento2/pull/13061)

## Archivos adjuntos
