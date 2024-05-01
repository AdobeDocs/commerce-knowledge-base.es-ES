---
title: Errores 403 al acceder a la herramienta de análisis de todo el sitio en Adobe Commerce
description: Este artículo proporciona una solución para los casos en los que reciba errores 403 al intentar acceder a la herramienta de análisis de todo el sitio en Adobe Commerce.
exl-id: f24fad17-62d6-4a0f-bcba-983c3dbee3d7
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Errores 403 al acceder a la herramienta de análisis de todo el sitio en Adobe Commerce

Este artículo proporciona una solución para los casos en los que reciba errores 403 al intentar acceder a la herramienta de análisis de todo el sitio en Adobe Commerce.

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube 2.4.1 y posterior.

## Problema

Se produce un error 403 al intentar acceder a la herramienta de análisis de todo el sitio.

<u>Pasos a seguir:</u>

Inicie sesión en el panel de administración de Commerce y haga clic en **Informes** > *System Insights* > **Herramienta de análisis de todo el sitio**.

<u>Resultado esperado:</u>

Verá la herramienta de análisis de todo el sitio.

<u>Resultado real:</u>

Verá lo siguiente: *Error 403.*


## Solución

Para asegurarse de que la herramienta de análisis de todo el sitio tiene el acceso adecuado a su aplicación, ejecute el siguiente comando en la CLI. Reemplazar `<store URL>` con la URL de la tienda:

```cURL
curl -sIL -X GET <store URL>/swat/key/index | grep HTTP
HTTP/2 403
```

Realice los pasos necesarios según el código de respuesta que obtenga.

### 403 Código de respuesta prohibido

Si el código de respuesta es 403, es posible que tenga la protección de bots de Cloudflare que está bloqueando la herramienta de análisis de todo el sitio. Para acceder a la herramienta, incluya sus direcciones IP en la lista blanca:

* 107.23.33.174
* 3 225 9 244
* 3 88 83 85

### Corrección del código de respuesta 200 y salida JSON

Si la respuesta es el código 200 correcto y la salida JSON, [enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para escalar el problema con el acceso a la herramienta de análisis de todo el sitio.


### 500 (Error grave) código de respuesta

Si un código de respuesta es 500 (error grave), instale el parche MDVA-38526. Utilice uno de los siguientes enlaces para descargar el parche, según el tipo de parche que desee:

* parche de Adobe Commerce en la infraestructura en la nube: [MDVA-38526_EE_2.4.1-p1_v3.patch.zip](assets/MDVA-38526_EE_2.4.1-p1_v3.patch.zip)
* parche del compositor de infraestructuras en la nube de Adobe Commerce: [MDVA-38526_EE_2.4.1-p1_COMPOSER_v3.patch.zip](assets/MDVA-38526_EE_2.4.1-p1_COMPOSER_v3.patch.zip)

El parche se aplica a Adobe Commerce en las versiones 2.4.1 y posteriores de la infraestructura en la nube.

### Respuesta no JSON

Si el resultado de la respuesta no es JSON, podría deberse a una implementación PWA/sin encabezado. Si utiliza la implementación sin encabezado, actualice la configuración UPWARD para evitar las solicitudes al origen de Adobe Commerce. Para ello, en el Administrador de Adobe Commerce, en **Tiendas** > **Configuración** > **General** > **Web** > **Configuración del PWA UPWARD** > **Lista de permitidos de nombre**, agregue *aplastar*.

![Upward_configuration](assets/upward_pwa.png)

Si sigue sin poder acceder a la herramienta de análisis de todo el sitio, la próxima vez que inicie sesión en el panel de administración de Commerce y vaya a **Informes** > *System Insights* > **Herramienta de análisis de todo el sitio**, [enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Lectura relacionada

* [Guía de la herramienta de análisis de todo el sitio](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html)
