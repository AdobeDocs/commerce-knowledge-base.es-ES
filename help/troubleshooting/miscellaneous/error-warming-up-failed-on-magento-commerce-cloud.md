---
title: "ERROR: error de calentamiento en Adobe Commerce en la infraestructura en la nube"
description: "Este artículo proporciona una solución para los casos en los que la caché de la página se esté calentando y falle con un error:"
exl-id: 20a88030-b1c9-4fdc-83c1-f344d44cd2e1
feature: Cache, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# ERROR: error de calentamiento en Adobe Commerce en la infraestructura en la nube

Este artículo proporciona una solución para cuando la caché de la página se calienta y falla con un error:

*ERROR: error en la preparación:`<website link>`*

## Productos y versiones afectados

* Adobe Commerce en la infraestructura de la nube, todas [las versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Error de calentamiento de la caché.

<u>Pasos a seguir</u>:

Iniciar operaciones de calentamiento de caché.

<u>Resultado esperado</u>:

Páginas o cargas de sitios completos.

<u>Resultado real</u>:

El sitio no está disponible o el tiempo de respuesta es demasiado alto. *ERROR: error en la preparación:`<website link>`*

## Causa

El calentamiento de la caché no funciona con el control de acceso HTTP habilitado.

## Solución

Asegúrese de que no tiene habilitado el control de acceso: vaya a la rama o entorno específico, haga clic en el icono **Configuración** y compruebe la configuración de **control de acceso HTTP**; en este caso, no se puede calentar la caché y hay que deshabilitar el control de acceso.

## Lectura relacionada

* [Guía del usuario de Adobe Commerce > Caché de página completa](https://docs.magento.com/user-guide/system/cache-full-page.html) en nuestra guía del usuario.
* [Calentamiento de la caché y sitio no disponible en Adobe Commerce](/help/troubleshooting/miscellaneous/cache-warming-up-and-site-unavailable-on-magento.md) en nuestra base de conocimiento de soporte.
