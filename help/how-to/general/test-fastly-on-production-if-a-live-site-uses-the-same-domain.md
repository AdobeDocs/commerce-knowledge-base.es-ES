---
title: Probar rápidamente en producción si un sitio activo utiliza el mismo dominio
description: Si tiene un sitio activo en funcionamiento en su dominio de producción (&grave;example.com&grave;) y necesita probar su nueva tienda en Adobe Commerce en el entorno de producción de la infraestructura de nube con Fastly CDN habilitado, recomendamos utilizar el subdominio (como &grave;prod.example.com&grave;), después de agregarlo anteriormente a Fastly, para cualquier actividad de prueba previa al lanzamiento. Este artículo analiza los detalles y proporciona vínculos útiles a los recursos de documentación de Adobe Commerce relacionados.
exl-id: bc9d11c8-ce47-461d-b5b8-c03494bc4ceb
feature: Cache
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%

---

# Probar rápidamente en producción si un sitio activo utiliza el mismo dominio

Si tiene un sitio activo en ejecución en su dominio de producción (`example.com`) y necesita probar su nueva tienda en Adobe Commerce en el entorno de producción de la infraestructura de nube con Fastly CDN habilitado, recomendamos utilizar el subdominio (como `prod.example.com`), después de agregarlo anteriormente a Fastly, para cualquier actividad de prueba previa al lanzamiento. Este artículo analiza los detalles y proporciona vínculos útiles a los recursos de documentación de Adobe Commerce relacionados.

## Problema

El almacén actual que usa el dominio de producción `example.com` está activo y en funcionamiento. Sin embargo, debe probar la nueva tienda, creada con Adobe Commerce en la infraestructura en la nube e implementada en el entorno de producción, con el servicio de caché de página completa de Fastly habilitado.

El problema es que el entorno de producción de su proyecto de infraestructura en la nube de Adobe Commerce usa el mismo dominio activo (`example.com`) y no puede cambiar el nuevo sitio a este dominio y, al mismo tiempo, tiene su tienda activa actual en ejecución, en el mismo dominio.

### ¿Por qué utilizar Fastly para pruebas en el entorno de producción?

En teoría, podría omitir el uso de Fastly CDN y probar su Adobe Commerce en el almacén de infraestructura en la nube en el entorno de producción sin habilitar la caché de página completa.

Sin embargo, con la caché de página completa habilitada, su tienda tiene un rendimiento diferente; nunca sabe el rendimiento real del sitio si no lo ha probado con CDN antes del lanzamiento. Probar su tienda en producción con Fastly CDN habilitado es la recomendación oficial de Adobe Commerce.

## Solución: utilice el subdominio de producción

Use el subdominio de primer nivel (`prod.example.com`) para el nuevo almacén de Adobe Commerce en la infraestructura en la nube en el entorno Producción mientras mantiene el sitio activo actual en el dominio base (`example.com`).

Al planificar el proyecto de infraestructura en la nube de Adobe Commerce, puede especificar dicho subdominio de producción y solicitar al equipo de infraestructura en la nube que dirija el subdominio al servicio de Fastly.

Siga estos pasos para procesar el subdominio dentro del proyecto de infraestructura en la nube de Adobe Commerce:

* [Envíe un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) solicitando agregar el subdominio a la configuración de Fastly service/Nginx (para la arquitectura de plan Pro de infraestructura en la nube de Adobe Commerce).
* Configure los ajustes de DNS correspondientes de su lado.

Después de realizar los pasos para la configuración del subdominio, también debe realizar estos pasos para validar el dominio de producción para el certificado SSL:

* Cargue el registro TXT DNS para la validación SSL del dominio de producción.
* [Envíe un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) solicitando validar el dominio de producción para el certificado SSL.

El uso del subdominio le permite realizar un &quot;inicio suave&quot; de su tienda en el futuro, ya que dicho inicio solo requiere actualizar la configuración DNS correspondiente.

## Documentación relacionada

En nuestra base de conocimiento de soporte:

* [Configurar rápidamente la configuración de DNS en los entornos de ensayo y producción](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/configure-fastly-dns-settings-on-staging-and-production-environments.html?lang=es)
* [Configurar Fastly para el plan de inicio en la nube](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/set-up-fastly-for-starter-plan-on-cloud.html?lang=es)
* [Bloqueadores potenciales para iniciarse en Adobe Commerce en la infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/blockers-launching-on-magento-commerce-cloud.html?lang=es)

En nuestra documentación para desarrolladores:

* [Información general rápida](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html?lang=es)
* [Activar lista de comprobación: configuraciones de DNS para Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html?lang=es)
