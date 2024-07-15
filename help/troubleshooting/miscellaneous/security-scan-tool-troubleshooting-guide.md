---
title: Guía de solución de problemas de Adobe Commerce Security Scan
description: Obtenga información sobre cómo solucionar los distintos problemas con la herramienta de análisis de seguridad para Adobe Commerce y Magento Open Source.
exl-id: 35e18a11-bda9-47eb-924a-1095f4f01017
feature: Compliance, Security
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 0%

---

# Guía de solución de problemas de Adobe Commerce Security Scan

Obtenga información sobre cómo solucionar los distintos problemas con la herramienta de análisis de seguridad para Adobe Commerce y Magento Open Source.

## Problema: No se puede enviar el sitio

La herramienta de análisis de seguridad requiere que pruebe que es el propietario del sitio antes de que se pueda agregar el dominio a la herramienta de análisis de seguridad. Para ello, agregue un código de confirmación al sitio mediante un comentario del HTML o la etiqueta `<meta>`. El comentario del HTML debe colocarse dentro de la etiqueta `<body>`, p. ej., en la sección de pie de página. La etiqueta `<meta>` debe colocarse dentro de la sección `<head>` de la página.

Un problema habitual que afrontan los comerciantes se produce cuando Security Scan Tool no puede confirmar la propiedad del sitio del comerciante.

Si recibe un error y no puede enviar su sitio para el análisis, consulte el [mensaje de error al agregar sitios al análisis de seguridad](/help/troubleshooting/miscellaneous/error-message-adding-site-into-security-scan.md) artículo de solución de problemas en nuestra base de conocimiento de asistencia.

## Problema: Informes vacíos generados por la herramienta de análisis de seguridad

Obtendrá informes de análisis vacíos de la herramienta de análisis de seguridad o informes que contengan solo un error, como *La herramienta de seguridad no pudo llegar a la URL base* o *No se encontró la instalación del Magento en la URL proporcionada*.

### Solución

1. Compruebe que las direcciones IP 52.87.98.44, 34.196.167.176 y 3.218.25.102 no estén bloqueadas en los puertos 80 y 443.
1. Compruebe la dirección URL enviada para obtener redirecciones (por ejemplo, `https://mystore.com` redirige a `https://www.mystore.com` o viceversa o redirige a otros nombres de dominio).
1. Investigue los registros de acceso de WAF/servidor web para solicitudes rechazadas/no satisfechas. HTTP 403 `Forbidden` y HTTP 500 `Internal server error` son las respuestas comunes del servidor que provocan la generación de informes vacíos. Este es un ejemplo del código de confirmación que bloquea las solicitudes de los agentes de usuario:

```code block
if(req.http.user-agent ~ "(Chrome|Firefox)/[1-7][0-9]" && client.ip !~ useragent_allowlist)

{   error 403;   }
```

También puede ver [El informe Herramienta de exploración de seguridad está en blanco](/help/troubleshooting/miscellaneous/the-security-scan-tool-report-is-blank.md) artículo en nuestra base de conocimiento de soporte técnico para obtener más información.

## Problema: Se ha resuelto el problema de seguridad, pero se sigue mostrando como vulnerable durante el análisis

Ha resuelto un problema de seguridad y espera que el análisis de seguridad muestre que ya no es vulnerable al problema recién resuelto. En su lugar, verá que el informe generado por el análisis de seguridad sigue indicándole que es vulnerable al problema de seguridad.

### Causa

Los metadatos de instancias de nube solo se recopilan para `active` y `live` proyectos de nube, y NO es un proceso en tiempo real.

El script de recopilación de estadísticas se ejecuta una vez al día y, a continuación, la herramienta de análisis de seguridad debe recoger los nuevos datos más adelante.

La latencia esperada del ciclo de sincronización es de hasta una semana y tarda un mínimo de 24 horas.

Los siguientes estados podrían aparecer en las comprobaciones:

1. **Paso**: la herramienta de exploración de seguridad ha analizado los datos actualizados y aprobado los cambios.
1. **Desconocido**: la herramienta de exploración de seguridad aún no tiene datos sobre su dominio. Espere al siguiente ciclo de sincronización.
1. **Error**: si el estado muestra error, deberá corregir el problema (habilite 2FA, cambie la dirección URL de administración, etc.) y espere al siguiente ciclo de sincronización.

Si han transcurrido 24 horas desde que se realizaron los cambios en la instancia y no se reflejan en el informe de análisis de seguridad, puede [enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Proporcione la dirección URL de la tienda al enviar el ticket.

## Error de BotNet Suspect

Recibirá una notificación con respecto al error &quot;Sospechoso de BotNet&quot;.

### Causa

1. El nombre de dominio de la tienda entró en una &quot;Lista de participantes potenciales de BotNet&quot; en 2019, y tenía el panel de administración, el descargador o la funcionalidad RSS expuesto públicamente, y/o su URL se ha mencionado en los foros de skimming CC.
1. La alerta podría estar causada por signos de compromiso con la tienda o malware, como JavaScript que se encuentra en la página.
1. No es necesariamente un problema en curso. Si la tienda se ha visto comprometida anteriormente, su nombre de host puede flotar alrededor de la web oscura como un nombre de &quot;víctima&quot;.
1. También puede deberse no a Adobe Commerce, sino a un compromiso del sistema (a nivel del sistema operativo).

### Solución

1. Compruebe las cuentas SSH recién creadas, los cambios en el sistema de archivos, etc.
1. Realice una revisión de seguridad.
1. Compruebe la versión y actualización de Adobe Commerce, especialmente si aún se está ejecutando el Magento 1, que ya no es compatible.
1. Si el problema continúa, [envíe un vale de soporte técnico](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) y proporcione la dirección URL de la tienda.

## Problema: Error de inyección de compromiso

Recibirá un error con respecto a un error de &quot;Inyección de compromiso&quot;.

### Solución

1. Revise las secuencias de comandos indicadas en el informe Herramienta de exploración de seguridad.
1. Revise el cuerpo de origen de la página de inicio para las inyecciones de scripts en línea.
1. Revise los cambios de configuración del sistema, especialmente los valores de sección `HTML head` y `Miscellaneous HTML` personalizados en `footer`.
1. Realice una revisión del código y la base de datos para detectar cambios y signos desconocidos de malware insertado.

Si nada de lo anterior ayuda, [envía un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) y proporciona la URL de la tienda y el mensaje de error del informe.

## Preguntas más frecuentes

### ¿Afectará el análisis de seguridad al rendimiento de mi sitio web?

No. El análisis de seguridad realiza todas las solicitudes una por una como un solo usuario. Debido a esto, el análisis de seguridad no debería afectar al rendimiento del sitio web.

### ¿Durante cuánto tiempo mantiene Adobe Commerce los informes de análisis de seguridad?

Puede generar los 10 informes anteriores desde su extremo. Si se requieren informes más antiguos, póngase en contacto con el soporte de Adobe Commerce. Se pueden obtener hasta un año de informes anteriores de análisis de seguridad.

### ¿Qué información se necesita al enviar un ticket de asistencia?

Asegúrese de proporcionar el nombre de dominio.
