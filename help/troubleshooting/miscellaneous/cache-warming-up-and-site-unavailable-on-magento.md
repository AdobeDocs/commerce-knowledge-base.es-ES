---
title: Calentamiento de la caché y sitio no disponible en Adobe Commerce
description: Este artículo proporciona una solución para cuando la caché de la página se calienta y hay una implementación atascada o un sitio inactivo.
exl-id: c91d5c1f-95e6-4240-be98-2acea49ae728
feature: Cache, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Calentamiento de la caché y sitio no disponible en Adobe Commerce

Este artículo proporciona una solución para cuando la caché de la página se calienta y hay una implementación atascada o un sitio inactivo.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, todas [versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problema

La secuencia de comandos de calentamiento de caché, al final de la fase posterior a la implementación, envía solicitudes a una velocidad tan alta que determinadas instancias, como las de 4 CPU, no pueden gestionarlas. Su nginx agota el número de trabajadores.

<u>Pasos a seguir</u>:

Iniciar operaciones de calentamiento de caché.

<u>Resultado esperado</u>:

Páginas o cargas de sitios completos.

<u>Resultado real</u>:

El sitio no está disponible o el tiempo de respuesta es demasiado alto.

## Solución

Limite el número de conexiones simultáneas durante el calentamiento de la caché. Esto requiere agregar la variable posterior a la implementación `WARM_UP_CONCURRENCY` para especificar el número de solicitudes de calentamiento que el script de calentamiento de caché puede enviar simultáneamente. Configurar esta opción puede ayudar a administrar la carga en la infraestructura en la nube de Adobe Commerce. Para ver los pasos, consulte [Post-deploy variables > WARM\_UP\_CONCURRENCY](https://devdocs.magento.com/cloud/env/variables-post-deploy.html#warm_up_concurrency) en nuestra documentación para desarrolladores.

## Lectura relacionada

[Caché de página completa](https://docs.magento.com/user-guide/system/cache-full-page.html) en nuestra guía del usuario
