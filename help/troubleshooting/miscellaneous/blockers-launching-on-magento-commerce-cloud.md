---
title: Bloqueadores que se inician en Adobe Commerce en la infraestructura en la nube
description: Este artículo proporciona una corrección para los bloqueadores que se inician en Adobe Commerce en la infraestructura en la nube, incluidos los problemas relacionados con la configuración de Fastly, los certificados SSL, las redirecciones 301 y el rendimiento de recursos estáticos.
exl-id: 3b2c331f-5d90-4051-ada1-4934538fce79
feature: Cache, Cloud, Marketing Tools, Observability, Paas
role: Developer
source-git-commit: 3dd44b72bc9f02fe808b70355c4331fc28aa3606
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 0%

---

# Bloqueadores que se inician en Adobe Commerce en la infraestructura en la nube

Este artículo proporciona una corrección para los bloqueadores que se inician en Adobe Commerce en la infraestructura en la nube, incluidos los problemas relacionados con la configuración de Fastly, los certificados SSL, las redirecciones 301 y el rendimiento de recursos estáticos.

## 1. Configuración rápida

[Rápido](https://www.fastly.com/) es una red de distribución de contenido (CDN) basada en Varnish que sirve recursos estáticos. Es necesario para Adobe Commerce en la infraestructura en la nube en entornos de producción, por lo que es importante configurar Fastly y probar el sitio web (UAT) con Fastly habilitado y configurado, tanto en entornos de ensayo como de producción.

>[!WARNING]
>
>Con Caché de página completa (FPC) habilitada, su sitio web tiene un rendimiento diferente; asegúrese de probarlo antes de publicarlo.

El proceso de configuración de Fastly se documenta en detalle en la [Configuración rápida](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) en nuestra guía del usuario. A continuación se presentan los pasos importantes.

### 1 bis. Asegúrese de que tiene instalada la versión más reciente del módulo Fastly

Asegúrese de tener instalada la versión más reciente del módulo Fastly para obtener las últimas funciones y mejoras. Para comprobar si tiene la versión más reciente de Fastly, consulte [Actualización del módulo de Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#upgrade-the-fastly-module) en nuestra guía del usuario. Para obtener más información, consulte [Configuración rápida](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) en nuestra guía del usuario.

### 1 ter. Habilitar y configurar Fastly con el administrador de Commerce

Para obtener más información, consulte [Obtenga sus credenciales de Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials) en nuestra guía del usuario.

### 1 quater. Cargar fragmentos de VCL de Fastly

Para obtener más información, consulte [Cargar VCL a Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) en nuestra guía del usuario.

También puede [crear y añadir sus propios fragmentos de VCL personalizados](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html).

### 1d. Configurar DNS para Fastly


Consulte este artículo para ver los pasos detallados: [Configuración rápida](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings) en nuestra guía del usuario.

### Artículos relacionados de Fastly en nuestra base de conocimiento de soporte

* [El almacenamiento en caché rápido no funciona en la nube](/help/troubleshooting/miscellaneous/fastly-caching-is-not-working-on-magento-cloud.md)
* [Error al purgar la caché de Fastly en la nube (la solicitud de purga no se procesó correctamente)](/help/troubleshooting/miscellaneous/error-purging-fastly-cache-on-cloud-the-purge-request-was-not-processed-successfully.md)

## 2. Certificado SSL (TLS) válido

Problema: Sin un certificado SSL válido y en funcionamiento, no puede probar métodos de pago externos en la página Cierre de compra, en el entorno de ensayo.

Recomendación **:** Solicite su certificado SSL compartido para los nombres de dominio de ensayo o activo.

Obtenga información sobre los certificados SSL en esta [Preguntas frecuentes rápidas](/help/announcements/adobe-commerce-announcements/magento-ssl-tls-certificate-requirements-and-clean-up.md) artículo en nuestra base de conocimiento de soporte.

## 3. Configurar y probar redirecciones 301

Problema: Las redirecciones 301 no se proporcionan o están mal configuradas, lo que provoca que su tienda caiga en los rankings SEO y en los listados de búsqueda.

Recomendación **:** Configure y pruebe cuidadosamente las redirecciones 301.

En caso de que esté migrando de un sitio web antiguo a uno nuevo, el 301 redirige a sus clientes de las páginas antiguas indexadas anteriormente a las páginas adecuadas de su nueva tienda, de esta manera:

http://www.mywebsite.com/old-category-page.html **>** http://www.mywebsite.com/new-seo-friendly-category-page.html

**Artículos relacionados:**

* [Redirecciones a través de routes.yaml](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/routes/redirects.html) en nuestra guía del usuario.
* [Redirecciones a través de la consola de Cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html) en nuestra guía del usuario.
* [Reescrituras de URL](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite.html) en nuestra guía del usuario.

## 4. Rendimiento de los activos

Problema: Los recursos estáticos se proporcionan lentamente, por lo que el sitio tiene un rendimiento deficiente (tiempo de carga prolongado, contenido multimedia no mostrado, etc.). Los recursos estáticos del sitio web son recursos CSS, imágenes, vídeos, documentos adjuntos y mucho más. La forma en que se organizan y atienden es un factor clave en el rendimiento del sitio.

Recomendación: Para identificar posibles causas de un rendimiento deficiente, considere la posibilidad de utilizar [Adobe Commerce Performance Toolkit](https://github.com/magento/magento2/tree/2.3/setup/performance-toolkit) para pruebas de rendimiento. También puede tener en cuenta estas herramientas de terceros:

* [Asedio](https://www.joedog.org/siege-home/): Utilidad de prueba de carga y pruebas de referencia HTTP; admite autenticación básica, cookies, protocolos HTTP, HTTPS y FTP.
* [Jmeter](https://jmeter.apache.org/): una herramienta de prueba de carga y medición del rendimiento de buena reputación. Ayuda a medir el rendimiento para el tráfico pico, por ejemplo, para las ventas flash.
* [New Relic](https://support.newrelic.com/): Localiza procesos y áreas del sitio que causan un rendimiento lento con un tiempo rastreado empleado por acción, como la transmisión de datos, consultas, Redis, etc.
* [WebPageTest](https://www.webpagetest.org/) (gratuito) y [PKingdom](https://www.pingdom.com/) (de pago): análisis en tiempo real del tiempo de carga de las páginas del sitio con diferentes ubicaciones de origen.

También puede considerar lo siguiente [minificación](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) para CSS, JavaScript y HTML.

**Artículos relacionados:**

* [Probar implementación](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production.html) en nuestra documentación para desarrolladores.
