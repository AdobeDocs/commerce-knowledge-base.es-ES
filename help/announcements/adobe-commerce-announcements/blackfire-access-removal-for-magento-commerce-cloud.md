---
title: Eliminación del acceso Blackfire para Adobe Commerce en la infraestructura en la nube
description: El 11 de abril de 2020, el acceso gratuito a la monitorización del rendimiento Blackfire ya no se incluirá con Adobe Commerce en la arquitectura del plan Pro de la infraestructura en la nube ni con Adobe Commerce en las suscripciones a la arquitectura del plan inicial de la infraestructura en la nube.  Ya no podrá iniciar sesión en su cuenta de Blackfire. Es posible seguir utilizando Blackfire más allá del 11 de abril comprando una licencia directamente a través de Blackfire.io. Los comerciantes de Adobe Commerce que no hayan adquirido licencias directamente de Blackfire en esa fecha tendrán desactivadas sus licencias de Blackfire gratuitas proporcionadas por el Adobe. Junto con esto, se desactivará la funcionalidad para crear nuevos informes con la herramienta Analizador. Los clientes que utilizan la arquitectura Pro alojada en la infraestructura en la nube pueden seguir recibiendo monitorización gratuita del rendimiento de la infraestructura a través de la infraestructura de New Relic.
exl-id: bf33c2c6-e9b3-474a-a127-909b51dff92f
feature: Cloud, Paas
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# Eliminación del acceso Blackfire para Adobe Commerce en la infraestructura en la nube

El 11 de abril de 2020, el acceso gratuito a la monitorización del rendimiento Blackfire ya no se incluirá con Adobe Commerce en la arquitectura del plan Pro de la infraestructura en la nube ni con Adobe Commerce en las suscripciones a la arquitectura del plan inicial de la infraestructura en la nube.  Ya no podrá iniciar sesión en su cuenta de Blackfire. Es posible seguir utilizando Blackfire más allá del 11 de abril comprando una licencia directamente a través de Blackfire.io. Los comerciantes de Adobe Commerce que no hayan adquirido licencias directamente de Blackfire en esa fecha tendrán desactivadas sus licencias de Blackfire gratuitas proporcionadas por el Adobe. Junto con esto, se desactivará la funcionalidad para crear nuevos informes con la herramienta Analizador. Los clientes que utilizan la arquitectura Pro alojada en la infraestructura en la nube pueden seguir recibiendo monitorización gratuita del rendimiento de la infraestructura a través de la infraestructura de New Relic.

**Si desea seguir usando el Blackfire**:

1. Debe adquirir una licencia directamente con Blackfire.
1. Luego configure el Blackfire siguiendo estos [pasos](https://blackfire.io/docs/integrations/paas/magentocloud).
1. Si experimenta algún problema con la instalación, [puede enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para solicitar asistencia. Para preguntas específicas del Blackfire, póngase en contacto con el soporte técnico del Blackfire directamente en [support@blackfire.io](mailto:support@blackfire.io).

## Si tiene errores al ejecutar una implementación:

Si al ejecutar una implementación obtiene errores relacionados con el Blackfire, haga lo siguiente:

1. Elimine el Blackfire de la configuración. Edite el archivo `.magento.app.yaml` y quite el Blackfire de la sección de tiempo de ejecución:

   ```YAML
   ...
   # Enable extensions required by Magento 2
   runtime:
     extensions:
     - redis
     - xsl
     - json
     -**blackfire**
      - imap
   ...
   ```

1. Complete esto en el entorno de desarrollo local y envíelo a la nube.

Solo [envía un ticket de soporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) si ves el siguiente error después de ejecutar una implementación:

*Advertencia de PHP: Inicio de PHP: No se puede cargar la biblioteca dinámica &#39;blackfire.so&#39; (intentado: /usr/lib/php/20180731-zts/blackfire.so (/usr/lib/php/20180731-zts/blackfire.so: no se puede abrir el archivo de objeto compartido: no existe ese archivo o directorio), /usr/lib/php/20180731-zts/blackfire.so.so (/usr/lib/php/20180731-zts/blackfire.so.so: no se puede abrir el archivo de objeto compartido: no existe ese archivo o directorio)) en Desconocido en la línea 0*

Este error significa que el complemento Blackfire debe actualizarse y evitar que se cargue.

**Si desea usar la infraestructura de New Relic**:

Para obtener información sobre cómo acceder a la infraestructura de New Relic, consulte [Acceder a New Relic](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) en nuestra base de conocimiento de asistencia.
