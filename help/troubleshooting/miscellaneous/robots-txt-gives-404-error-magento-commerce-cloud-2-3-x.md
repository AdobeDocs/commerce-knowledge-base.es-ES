---
title: 'robots.txt: error 404 de Adobe Commerce en la infraestructura en la nube'
description: Este artículo proporciona una corrección para el caso en el que el archivo robots.txt genera un error 404 en Adobe Commerce en la infraestructura en la nube.
exl-id: 6f0b9f47-1901-4c43-88d8-fd992015d70f
feature: Cloud, Marketing Tools, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# robots.txt: error 404 de Adobe Commerce en la infraestructura en la nube

Este artículo proporciona una corrección para cuando la variable `robots.txt` genera un error 404 en Adobe Commerce en la infraestructura de la nube.

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube (todas las versiones)

## Problema

El `robots.txt` El archivo no funciona y genera una excepción Nginx. El `robots.txt` se genera dinámicamente &quot;sobre la marcha&quot;. El `robots.txt` no es accesible para el archivo `/robots.txt` URL porque Nginx tiene una regla de reescritura que redirige a la fuerza todas las `/robots.txt` solicitudes a `/media/robots.txt` archivo que no existe.

## Causa

Esto suele ocurrir cuando Nginx no está configurado correctamente.

## Solución

La solución es deshabilitar la regla Nginx que redirige `/robots.txt` solicitudes a `/media/robots.txt` archivo. Los comerciantes con un autoservicio habilitado pueden hacerlo por su cuenta y los comerciantes sin un autoservicio habilitado deben crear un vale de soporte.

Si no tiene habilitado el autoservicio (o no está seguro de si lo tiene habilitado), [enviar un ticket de asistencia al Magento](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) solicitar la eliminación de la regla de redirección de Nginx de `/robots.txt` solicitudes a `/media/robots.txt`.

Si tiene habilitado el autoservicio, actualice ECE-Tools al menos a 2002.0.12 y elimine la regla de redireccionamiento Nginx en su `.magento.app.yaml` archivo. Puede hacer referencia a [Añadir robots de mapa del sitio y de motor de búsqueda](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap.html) en nuestra documentación para desarrolladores para obtener más información.

## Lectura relacionada

* [Cómo bloquear el tráfico malicioso para el Magento Commerce Cloud en el nivel de Fastly](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) en nuestra base de conocimiento de soporte.
* [Añadir robots de mapa del sitio y de motor de búsqueda](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) en nuestra documentación para desarrolladores.
* [Robots del motor de búsqueda](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots) en nuestra guía del usuario.
