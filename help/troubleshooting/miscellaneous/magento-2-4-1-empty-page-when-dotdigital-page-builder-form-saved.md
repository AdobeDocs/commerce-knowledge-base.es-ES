---
title: "Adobe Commerce 2.4.1: página vacía cuando se guardó el formulario dotdigital Page Builder"
description: Este artículo proporciona una solución para un problema conocido de Adobe Commerce 2.4.1 que se producía al mostrar una página web vacía después de guardar un formulario de Page Builder digital de puntos en el Panel de administración al utilizar el explorador Safari.
exl-id: 682eac73-1ad2-4093-acfb-6a8da4c05cf5
feature: Page Builder
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Adobe Commerce 2.4.1: página vacía al guardar el formulario dotdigital de Page Builder

Este artículo proporciona una solución para un problema conocido de Adobe Commerce 2.4.1 que se producía al mostrar una página web vacía después de guardar un formulario de Page Builder digital de puntos en el Panel de administración al utilizar el explorador Safari.

## Productos y versiones afectados

* Adobe Commerce local 2.4.1
* Adobe Commerce en la infraestructura en la nube 2.4.1

## Problema

<u>Pasos a seguir</u>

1. Vaya a **Panel de administración** > **Contenido** > **Páginas** y seleccione **Editar** de cualquier página.
1. Vaya a **Contenido** y haga clic en el botón **Editar con Page Builder**.
1. Arrastre el bloque **dotdigital form** y seleccione **Editar**.
1. Seleccione uno de los formularios de prueba, luego elija el modo **Incrustado** y guarde el formulario.
1. Guarde la modificación de la página.

<u>Resultado esperado:</u>

La página web debe guardarse correctamente.

<u>Resultado real:</u>

La página web está vacía. Después de volver a cargar la página web, se aplican los cambios.

## Solución

La solución consiste en utilizar un explorador alternativo a Safari. Está previsto que el problema se solucione en la próxima versión, Adobe Commerce 2.4.2, en el primer trimestre de 2021.

## Lectura relacionada

* [¿Qué es Page Builder?](https://developer.adobe.com/commerce/frontend-core/page-builder/) en nuestra documentación para desarrolladores.
* [Configuración de Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/setup.html?lang=es) en nuestra documentación para desarrolladores.
* [Generador de páginas](https://experienceleague.adobe.com/es/docs/commerce-admin/page-builder/introduction) en nuestra guía del usuario.
* [Page Builder: elementos](https://experienceleague.adobe.com/es/docs/commerce-admin/page-builder/workspace#elements) en nuestra guía del usuario.
