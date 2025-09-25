---
title: Bloquear el tráfico malintencionado para Adobe Commerce en el nivel Rápido
description: En este artículo se explican los pasos que puede seguir para bloquear el tráfico malintencionado cuando sospeche que el almacén de Adobe Commerce en la infraestructura de la nube está experimentando un ataque DDoS.
exl-id: 1a834a0a-753b-432e-9c3b-ef8dd034d294
feature: Cache, Marketing Tools
source-git-commit: 2555fbdb8a7a53d41c746df6414a7b0bad2de5d9
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 0%

---

# Bloquear el tráfico malintencionado para Adobe Commerce en el nivel Rápido

Este artículo explica cómo bloquear el tráfico no deseado en su tienda, no solo en respuesta a amenazas maliciosas, sino también como un método de filtrado geográfico.

Adobe Commerce en la infraestructura en la nube (y Fastly CDN) proporciona herramientas para administrar el tráfico a su tienda en respuesta a amenazas maliciosas como ataques DDoS. Además, permite bloquear solicitudes de países o regiones específicos, incluso si no se detecta ninguna intención maliciosa, para cumplir con políticas comerciales, requisitos regulatorios u otras necesidades operativas.

## Productos y versiones afectados:

* Adobe Commerce en la infraestructura en la nube 2.3.x

En este artículo asumimos que ya tiene las IP maliciosas y/o sus agentes de país y usuario. Los usuarios de Adobe Commerce en la infraestructura en la nube suelen obtener esta información del servicio de asistencia de Adobe Commerce. Las secciones siguientes proporcionan los pasos para bloquear el tráfico en función de esta información. Todos los cambios deben realizarse en el entorno Producción.

## Obtener acceso al Panel de administración

Si el sitio web está sobrecargado por DDoS, es posible que no pueda iniciar sesión en el administrador de Commerce (y realizar todos los pasos descritos más adelante en este artículo).

Para obtener acceso al administrador, ponga su sitio web en modo de mantenimiento como se describe en [Habilitar o deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) y coloque en la lista blanca su dirección IP. Desactive el modo de mantenimiento una vez finalizado este proceso.

## Bloquear tráfico por dirección IP

En el caso del almacén de infraestructura en la nube de Adobe Commerce, la forma más eficaz de bloquear el tráfico mediante direcciones IP y subredes específicas es añadir una ACL para Fastly en el administrador de Commerce. A continuación se indican los pasos con vínculos a instrucciones más detalladas:

1. En el Administrador de Commerce, vaya a **Tiendas** > **Configuración** > **Avanzado** > **Sistema** > **Caché de página completa** > **Configuración rápida**.
1. [Cree una nueva ACL](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/ACL.md) con una lista de direcciones IP o subredes que va a bloquear.
1. Añádalo a la lista de ACL y bloquéelo como se describe en la guía [Bloqueo](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) para el módulo Fastly\_Cdn para Adobe Commerce.

## Bloquear tráfico por país

Para el almacén de infraestructura en la nube de Adobe Commerce, la forma más eficaz de bloquear el tráfico por país es añadir una ACL para Fastly en el administrador de Commerce.

1. En el Administrador de Commerce, vaya a **Tiendas** > **Configuración** > **Avanzado** > **Sistema** > **Caché de página completa** > **Configuración rápida**.
1. Seleccione los países y configure el bloqueo mediante ACL como se describe en la guía [Bloqueo](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) para el módulo Fastly\_Cdn para Adobe Commerce.

## Bloquear tráfico por agente de usuario

Para establecer un bloqueo basado en el agente de usuario, debe agregar un fragmento de VCL personalizado a la configuración de Fastly. Para ello, siga los siguientes pasos:

1. En el Administrador de Commerce, vaya a **Tiendas** > **Configuración** > **Avanzado** > **Sistema** > **Caché de página completa**.
1. A Continuación, **Configuración Rápida** > **Fragmentos De VCL Personalizados**.
1. Cree el nuevo fragmento personalizado como se describe en la guía [Fragmentos personalizados de VCL](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/CUSTOM-VCL-SNIPPETS.md) para el módulo Fastly\_Cdn. Puede utilizar el siguiente ejemplo de código como ejemplo. Este ejemplo deshabilita el tráfico para los agentes de usuario `AhrefsBot` y `SemrushBot`.

```php
name: block_bad_useragents
  type: recv
  priority: 5
  VCL:
  if ( req.http.User-Agent ~ "(AhrefsBot|SemrushBot)" ) {
      error 405 "Not allowed";
  }
```

## Limitación de velocidad (funcionalidad experimental de Fastly)

Hay una funcionalidad experimental de Fastly para Adobe Commerce en la infraestructura de la nube que le permite especificar el límite de velocidad para rutas y rastreadores particulares. Consulte la [documentación del módulo Fastly](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/RATE-LIMITING.md) para obtener más información.

La funcionalidad debe probarse exhaustivamente en el ensayo antes de utilizarse en la producción, ya que podría bloquear el tráfico legítimo.

## Recomendado: considere actualizar robots.txt

La actualización del archivo de `robots.txt` podría ayudar a evitar que ciertos motores de búsqueda, rastreadores y robots rastreen determinadas páginas. Algunos ejemplos de páginas que no se deben rastrear son las páginas de resultados de búsqueda, cierre de compra, información del cliente, etc. Evitar que los robots rastreen estas páginas podría ayudar a disminuir el número de solicitudes generadas por esos robots.

Hay dos consideraciones importantes al usar `robots.txt`:

* Los robots pueden ignorar su `robots.txt`. Especialmente los robots de malware, que analizan la web en busca de vulnerabilidades de seguridad, y los recolectores de direcciones de correo electrónico utilizados por los remitentes de spam no prestarán atención.
* El archivo `robots.txt` es un archivo disponible públicamente. Cualquiera puede ver qué secciones de su servidor no quiere que utilicen los robots.

La información básica y la configuración predeterminada de Adobe Commerce `robots.txt` se encuentran en el artículo [Robots de motores de búsqueda](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/seo/seo-overview#search-engine-robots) de nuestra documentación para desarrolladores.

Para obtener información general y recomendaciones acerca de `robots.txt`, vea:

* [Crear un archivo robots.txt](https://developers.google.com/search/docs/advanced/robots/create-robots-txt) por el equipo de asistencia de Google
* [Acerca de /robots.txt](https://www.robotstxt.org/robotstxt.html) por robotstxt.org

Póngase en contacto con su desarrollador o con su experto en SEO para determinar qué agentes de usuario desea permitir o qué agentes de usuario desea impedir.

## Lectura relacionada

* [Términos de licencia específicos del producto para Adobe Commerce en la nube](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/PSLT-AdobeCommerceCloud-WW-2023v1.pdf)
* [VCL personalizado para bloquear solicitudes](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/custom-vcl-snippets/fastly-vcl-blocking) en la Guía de Commerce en la nube
