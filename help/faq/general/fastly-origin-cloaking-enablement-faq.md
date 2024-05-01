---
title: "[!DNL Fastly] origin cloaking enablement FAQ"
description: Estas preguntas frecuentes tratan sobre lo siguiente [!DNL Fastly] habilitación de la ocultación de origen en Adobe Commerce (que se implementó completamente a partir de 2021).
exl-id: d608abe7-7d64-44ce-bea1-34b201c29113
source-git-commit: 348a1f6e455aff9ad7c562ea20c95f27c9ee0b86
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# [!DNL Fastly] preguntas frecuentes sobre origin cloaking enablement

Estas preguntas frecuentes tratan sobre lo siguiente [!DNL Fastly] habilitación de la ocultación de origen en Adobe Commerce (que se implementó completamente a partir de 2021).

## Qué es [!DNL Fastly] ¿encubrimiento de origen?

El encubrimiento de origen es una función de seguridad que permite a Adobe Commerce en la infraestructura de la nube bloquear cualquier [!DNL non-Fastly] tráfico (para evitar ataques DDoS, vaya a la infraestructura en la nube (origen).

## ¿Cuáles son los beneficios del encubrimiento de origen?

El encubrimiento de origen está diseñado para evitar que el tráfico omita el [!DNL Fastly Web Application Firewall] (WAF) y enrutarlo a través del flujo estrictamente definido de **[!DNL Fastly]** > **Equilibrador de carga** > **Instancias**. Con esta implementación, se garantiza que todo el tráfico pase por el [!DNL Fastly] WAF, así como el WAF interno integrado en el equilibrador de carga.

## ¿Por qué se produce esta habilitación del encubrimiento de origen?

Esta función se creó originalmente para beneficiar a Adobe Commerce en la infraestructura en la nube.

## ¿Debo solicitar la habilitación del encubrimiento de origen para mi proyecto?

No. Esta función ya debería haberse implementado en todos los proyectos de la nube y cualquier proyecto que se haya aprovisionado desde 2021 tendría esto habilitado de forma predeterminada. Sin embargo, puede solicitar que se deshabilite el encubrimiento de origen para su proyecto mediante [enviar una solicitud de asistencia](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## ¿El encubrimiento de origen cambia la dirección IP saliente?

No, no lo hace.

## ¿Afecta el encubrimiento de origen a la API de REST?

[!DNL Fastly] no almacena en caché las llamadas a la API, por lo que el cliente debería estar de acuerdo con el cambio. El encubrimiento de origen solo bloquea las solicitudes que van directamente al origen, como:

```php
mywebsite.com.c.abcdefghijkl.ent.magento.cloud
```

En este ejemplo, el cliente aún puede acceder a la API si cambia la dirección URL a ``mywebsite.com``:

```php
mywebsite.com/rest/default/V1/integration/admin/token?username=XXXX&password=XXXXX;
mywebsite.com/rest/default/V1/orders/
mywebsite.com/rest/default/V1/products/
mywebsite.com/rest/default/V1/inventory/source-items
```

## ¿Afectará este cambio a la implementación y al tiempo de inactividad?

No, este cambio sí **NO** implementación de impacto y tiempo de inactividad.

## Si el proyecto tiene varios entornos de ensayo, ¿se aplicará el encubrimiento de origen a todos los entornos de ensayo?

Sí, si el proyecto tiene varios entornos de ensayo, el cambio se aplicará a todos los entornos de ensayo.
