---
title: "Cortafuegos de aplicaciones web (WAF) con tecnología Fastly: las preguntas frecuentes"
description: Los firewalls de aplicaciones web (WAF) evitan que el tráfico malintencionado entre en sitios y redes filtrando el tráfico con un conjunto de reglas de seguridad. Déclencheur El tráfico que infringe cualquiera de las reglas se bloquea antes de que pueda dañar los sitios o la red.
exl-id: d977ea68-7d8c-4863-b026-acdc25d8c430
feature: Cache
source-git-commit: f384ff9d5d8a8c5c5da20b582c02a2d783b32d7e
workflow-type: tm+mt
source-wordcount: '1654'
ht-degree: 0%

---

# Firewall de aplicaciones web (WAF) con tecnología Fastly: preguntas frecuentes

## ¿Cómo funciona el WAF en la nube administrado de Adobe Commerce (con tecnología de Fastly)?

Los firewalls de aplicaciones web (WAF) impiden que [tráfico malintencionado](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) entre en sitios y redes filtrando el tráfico en un conjunto de reglas de seguridad. Déclencheur El tráfico que infringe cualquiera de las reglas se bloquea antes de que pueda dañar los sitios o la red.

El WAF en la nube de Adobe Commerce proporciona una política de WAF con un conjunto de reglas diseñado para proteger las aplicaciones web de Adobe Commerce de una amplia gama de ataques.

La WAF examina el tráfico web y de administración para identificar cualquier actividad sospechosa. Evalúa el tráfico de GET y de POST (llamadas a la API HTTP) y aplica el conjunto de reglas para determinar qué tráfico bloquear. El WAF puede bloquear una amplia variedad de ataques, incluidos ataques de inyección SQL, ataques de scripts entre sitios, ataques de exfiltración de datos y violaciones del protocolo HTTP.

Como servicio basado en la nube, WAF no requiere hardware ni software para instalar o mantener. Fastly, un socio tecnológico existente, proporciona el software y la experiencia. Su WAF de alto rendimiento y siempre activo reside en cada nodo de caché en la red de entrega global de Fastly.

## ¿Está disponible el WAF para todos los clientes de la nube?

Sí, el servicio WAF en la nube está incluido en su suscripción a Adobe Commerce en la infraestructura en la nube tanto para los planes de Adobe Commerce en la infraestructura en la nube de la arquitectura del plan inicial como para los planes de Adobe Commerce en la infraestructura en la nube de la arquitectura del plan Pro sin coste adicional. El servicio WAF está disponible en los entornos Producción y Ensayo.

## ¿WAF cumple los requisitos de PCI DSS 6.6?

Sí.

## Si mi cuenta de Adobe Commerce en la infraestructura de la nube administra sitios en varios dominios, ¿está ajustado el perfil WAF para cada dominio o colectivamente para todos?

El WAF se ajusta colectivamente para todos los dominios en una sola cuenta de nube.

## ¿Qué reglas se utilizan para el WAF?

El conjunto de reglas del perfil WAF aplicado a su entorno de producción de infraestructura en la nube de Adobe Commerce se basa en el conjunto de reglas de Protección contra amenazas de OWASP Top 10, que cubre las vulnerabilidades comunes a los servicios web. También contiene reglas específicas de Adobe Commerce desarrolladas por TrustWave SpiderLabs. El equipo de investigación de seguridad de Fastly también ha agregado reglas que protegen su sitio y red de ataques comúnmente conocidos: direcciones IP incorrectas, agentes de usuario incorrectos y nodos de comando y control de botnet conocidos. Habilitamos reglas en OWASP Paranoia Nivel 3 o menos, que proporciona cobertura de alta seguridad.

## ¿Cómo puedo acceder a los registros?

Para que los registros se envíen a su herramienta de registro, trabaje con el administrador de cuentas técnico (TAM) para agregar un punto final de registro en Fastly.

## ¿Qué aspecto tiene una solicitud de bloqueo?

Una solicitud bloqueada devuelve una página 403 con un identificador de solicitud.

Puede personalizar esta página siempre que la personalización incluya el identificador de solicitud. Póngase en contacto con el administrador técnico de cuentas para obtener más información.

## ¿Cómo se actualizan los conjuntos de reglas WAF? ¿Con qué rapidez se puede cambiar o actualizar una regla WAF y aplicarla globalmente en producción?

Como parte del servicio WAF en la nube, Fastly gestiona las actualizaciones de reglas de terceros comerciales, investigaciones de Fastly y fuentes abiertas. Actualizan las reglas publicadas en una directiva según sea necesario o cuando los cambios en las reglas están disponibles en sus respectivas fuentes. Las nuevas reglas que coinciden con las clases de reglas publicadas también se insertan en la instancia WAF de cualquier servicio una vez que se ha habilitado. Esto ayuda a garantizar una cobertura inmediata para las vulnerabilidades nuevas o en evolución. Puede revisar la información [sobre actualizaciones y mantenimiento de reglas](https://docs.fastly.com/guides/web-application-firewall/fastly-waf-rule-set-updates-maintenance#rule-set-maintenance) en el sitio de documentación de Fastly.

## ¿En qué se diferencia el WAF en la nube de Adobe Commerce de la solución WAF que ofrece Fastly a sus clientes directos?

La solución WAF que vende directamente Fastly es una oferta de pago que incluye conjuntos de reglas más amplios y funciones adicionales como personalización de reglas y protección contra malware. La solución WAF en la nube de Adobe Commerce incluye un subconjunto de reglas dirigidas a la aplicación Adobe Commerce e incluye solo un conjunto de reglas para cada entorno de producción del cliente.

## ¿Contra qué tipos de amenazas de seguridad protege WAF?

<table class="table-basic" style="width: 649px;">
<tbody>
<tr>
<th style="width: 145.5px; text-align: left;">Amenaza</th>
<th style="width: 497.5px; text-align: left;">Protección WAF</th>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Ataques de inyección SQL</td>
<td style="width: 497.5px;">Tanto el conjunto de reglas principales de OWASP ModSecurity como el conjunto de reglas comerciales TrustWave incluyen filtros específicos para ataques de inyección de SQL y sus variantes.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">
<p>Inyección en sitios múltiples</p>
</td>
<td style="width: 497.5px;">El conjunto de reglas OWASP protege contra ataques de inyección entre sitios. Fastly aprovecha un mecanismo de puntuación para cada solicitud que busca una inyección entre sitios y otras amenazas al origen. Puntuamos cada solicitud con todo el conjunto de reglas principal y validamos que la puntuación de la solicitud se encuentra por debajo de un umbral configurable para que se apruebe.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Ataques por fuerza bruta</td>
<td style="width: 497.5px;">Cubierto por el conjunto de reglas de OWASP. Fastly también bloquea la actividad de fuerza bruta mediante el uso de código VCL que reconoce fuentes, solicitudes o intentos específicos de fuerza bruta o de saturar los controles de seguridad antes de que cualquier tráfico llegue al centro de datos de origen.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Ataques de red</td>
<td style="width: 497.5px;">Los ataques de red, o ataques dirigidos a la infraestructura de red, son administrados automáticamente por Fastly. Fastly no pasa DNS al origen y el tráfico que no coincide con un perfil HTTP, HTTPS o DNS estrecho se descarta en el borde de la red. Los ataques dirigidos a protocolos de control se defienden mediante la autenticación de puntos finales en toda la red. Además, los protocolos de red utilizados dentro de la red de Fastly se endurecen para garantizar que no se puedan aprovechar como medio de amplificación o reflexión. Los clientes son responsables de la protección contra ataques que omiten la red de Fastly mediante el uso del espacio de direcciones IP de caché de Fastly, publicado a nuestros clientes como componente de nuestro servicio de CDN. Se recomienda que el espacio de direcciones IP de origen no se publique en DNS públicos para garantizar que los ataques de omisión no puedan utilizar estas direcciones como objetivos.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Ataques de inyección de JavaScript</td>
<td style="width: 497.5px;">Las reglas WAF protegen contra el código JavaScript malintencionado que se inserta en las comunicaciones del cliente con los servicios web. Los patrones o puntuaciones de explotación comunes se filtran a través de WAF para garantizar la integridad del servicio de origen.</td>
</tr>
</tbody>
</table>

## ¿Se ofrecen funciones y características adicionales?

La oferta WAF de Adobe Commerce incluye protección contra las 10 principales amenazas de OWASP como parte de los requisitos de PCI, compatibilidad las 24 horas del día, los 7 días de la semana, incluida la evaluación de falsos positivos y las actualizaciones de la versión. Las siguientes funciones no son compatibles con la oferta estándar:

* limitación velocidad
* personalizaciones de reglas
* mitigación de bots
* protección contra malware

## ¿Cómo afecta el rendimiento de mi sitio el WAF?

Se estima que cada solicitud sin caché tiene de 1,5 milisegundos (ms) a 20 ms de latencia.

## ¿Pueden los clientes crear y modificar listas negras de IP para bloquear el tráfico?

Sí, los clientes pueden habilitar el bloqueo por país y acceder a la lista de control (ACL) desde Adobe Commerce en la interfaz de usuario de administración de la infraestructura de la nube. Utilice estas funciones en casos en los que desee bloquear el acceso de visitantes procedentes de países específicos o determinadas direcciones IP o intervalos de IP. Si desea que los visitantes bloqueados vean una página personalizada en lugar de un código de error, puede crear una página de error personalizada cargando el HTML en el menú Configuración rápida. Consulte [Crear una página de error/mantenimiento personalizada](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=es) en nuestra documentación para desarrolladores.

## ¿Dónde puedo comprobar el estado operativo de mi servicio WAF?

La disponibilidad general del servicio WAF se indica en la [página de estado rápido](https://status.fastly.com/). No se han proporcionado informes de disponibilidad para el WAF de clientes individuales.

## ¿Adobe Commerce proporciona la administración de incidentes para el servicio WAF?

En este momento no se ofrece la administración de incidentes.

## ¿Adobe Commerce tiene un centro de operaciones de seguridad?

Aunque Adobe Commerce no tiene un Centro de Operaciones de Seguridad, tenemos un proceso de operaciones de seguridad que nos permite emplear los recursos adecuados para responder a los incidentes de seguridad en tiempo real. También ofrecemos soporte de seguimiento del sol 24/7/365.

También puedes obtener noticias y actualizaciones de seguridad relacionadas con Adobe Commerce en [Centro de seguridad](https://helpx.adobe.com/es/security.html).

## ¿Qué soporte está disponible?

La compatibilidad con WAF ofrece los siguientes recursos para ayudarle a mitigar los impactos del servicio de las solicitudes no deseadas o malintencionadas:

* Incorporación: activación, configuración inicial y monitorización limitada de los servicios de Fastly que admiten el WAF en la nube administrado por Adobe Commerce
* Clasificación de falsos positivos en curso para tratar casos en los que el WAF bloquea el tráfico legítimo
* Configuración de cualquier regla estándar nueva introducida como parte de las actualizaciones de la versión de WAF

Consulte los términos de [SLA en la nube](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Magento-Support-Services-Terms-and-Conditions.pdf) para obtener información de soporte adicional, incluidas definiciones de gravedad, tiempos de respuesta, canales y disponibilidad.

## Si el WAF está bloqueando el tráfico legítimo o causando otros problemas, ¿cómo puedo obtener ayuda?

[Envíe un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) en el [Centro de ayuda de Adobe Commerce](https://support.magento.com). Indique que el ticket está relacionado con el servicio WAF e incluya el identificador (ID) de solicitud bloqueado.

El sistema de tickets de asistencia de Adobe Commerce rastrea la comunicación entre nuestros ingenieros de asistencia y el personal de un cliente. Este sistema proporciona una transcripción con marca de tiempo de las comunicaciones y envía correos electrónicos al cliente y al personal de Adobe Commerce a medida que se actualizan los tickets.

Para todos los incidentes enviados en línea, la recepción del incidente se confirmará a través del sistema de tickets del Centro de ayuda al cliente de Adobe Commerce. Una vez recibido un incidente debidamente presentado, se dará prioridad a los servicios de apoyo de acuerdo con los niveles de prioridad establecidos anteriormente.

La siguiente tabla resume los canales de soporte y la disponibilidad para el Soporte de WAF:

<table class="table-basic">
<tbody>
<tr>
<th>Soporte técnico</th>
<th>Detalles</th>
</tr>
<tr>
<td>Ayuda de autoservicio en línea</td>
<td>Acceso ilimitado</td>
</tr>
<tr>
<td>Disponibilidad para informes de incidentes</td>
<td>24/7</td>
</tr>
<tr>
<td>Portal web</td>
<td>Disponible a través de Zendesk</td>
</tr>
<tr>
<td>Escalación de emergencia*</td>
<td>Consulte el artículo de la <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/adobe-commerce-p1-notification-hotline.html?lang=es">línea directa de notificaciones P1 de Adobe Commerce</a> para obtener números de Estados Unidos e internacionales.</td>
</tr>
</tbody>
</table>

*\* La línea telefónica de asistencia gratuita de Adobe Commerce está reservada únicamente para incidentes de prioridad 1. Las llamadas que no son de prioridad 1 ralentizarán la respuesta general a los problemas*

## ¿Cómo se clasifican los falsos positivos?

Tenemos un proceso de clasificación de falsos positivos (disponible las 24 horas del día, los 7 días de la semana) para abordar y resolver rápidamente las instancias en las que las solicitudes legítimas han activado una regla WAF. Los eventos de falso positivo se tratan como problemas de prioridad 1. Como acción predeterminada, nuestro equipo de soporte puede actualizar la directiva WAF inmediatamente para deshabilitar la regla que activó el evento de bloqueo y permitir que la solicitud legítima pase a través de WAF.

## ¿Qué sucede si el tráfico a la sección de administración de Adobe Commerce en los déclencheur del sitio de la infraestructura en la nube cumple las reglas WAF? ¿Resolverá el soporte de Adobe Commerce los problemas con el tráfico de administración bloqueado?

Sí, el tráfico de administración bloqueado se trata como un problema de prioridad 1.
