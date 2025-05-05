---
title: Solucionador de problemas de Adobe Commerce Fastly
description: Este solucionador de problemas de Fastly para los usuarios de Adobe Commerce le guiará a las soluciones, en función de su respuesta acerca de los síntomas que ve. Haga clic en las preguntas para ver las siguientes opciones o respuestas.
exl-id: c5c51b89-5a7d-49ba-a0ee-7abbaf78fdad
feature: Support, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# Solucionador de problemas de Adobe Commerce Fastly

Este solucionador de problemas de Fastly para los usuarios de Adobe Commerce le guiará a las soluciones, en función de su respuesta acerca de los síntomas que ve. Haga clic en las preguntas para ver las siguientes opciones o respuestas.

## Paso 1: Verificar el servicio de Fastly {#step-1}

+++**El cliente informa de un problema que implica a Fastly. ¿Está inactivo el servicio de Fastly?**

a. SÍ: comprueba [el estado del servicio Fastly](https://status.fastly.com/) y [envía un ticket de asistencia de Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Continúe con [Paso 2](#step-2).

+++

## Paso 2: Comprobación del archivo de configuración de VCL {#step-2}

+++**¿Tiene algún error al ejecutar el comprobador back-end?**

Ejecute la dirección URL del proyecto mediante el [Comprobador back-end - Fastly](https://magento-tester.global.ssl.fastly.net/magento-tester/). Muestra la versión del archivo de configuración de VCL, si la página se puede almacenar en caché, la versión del módulo de Fastly y otra información útil para solucionar problemas. ¿Tiene algún error?

a. SÍ - Tiene el mensaje _La versión del complemento VCL está obsoleta. Vuelva a cargarlo._ Para obtener la solución a este error, consulte [Error de Fastly: La versión de VCL del complemento está obsoleta. Vuelva a subir](/help/troubleshooting/miscellaneous/fastly-error-plugin-vcl-version-is-outdated-please-re-upload.md).\
b. NO - [Paso 3](#step-3).

+++

## Paso 3: Comprobación de errores de optimización de imágenes {#step-3}

+++**¿Error de optimización de imagen?**

a. SÍ: [Error al habilitar la optimización de imágenes](/help/troubleshooting/miscellaneous/error-enabling-image-optimization-in-magento-commerce.md).\
b. NO: compruebe el DNS ejecutando la CLI/terminal: `dig [your website.com] + short`. Continúe con [Paso 4](#step-4).

+++

## Paso 4: Verificación de DNS {#step-4}

+++**¿Qué sucede cuando se ejecuta `dig`?**

Cuando ejecutó `dig`, ¿devolvió un registro que apuntaba a prod.magentocloud.map.fastly.net o a una de las siguientes direcciones IP (consulte [Actualizar la configuración de DNS con la configuración de producción](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/launch/checklist#update-dns-configuration-with-production-settings) en nuestra documentación para desarrolladores):

* 151.101.1.124
* 151 101 65 124
* 151 101 129 124
* 151 101 193 124

a. SÍ: el problema no está relacionado con DNS. Continúe con [Paso 5](#step-5).\
b. NO: es probable que el problema esté relacionado con DNS. El cliente debe [comprobar la configuración de DNS](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/launch/checklist#update-dns-configuration-with-production-settings) o ponerse en contacto con su proveedor de DNS para obtener más información.

+++

## Paso 5: Confirmación de la conexión {#step-5}

+++**¿Recibe un mensaje &quot;Conexión no segura&quot; o &quot;No segura&quot; devuelto al ejecutar `curl -svo /dev/null "https://website.com"` en CLI/terminal?**

a. SÍ: es probable que se trate de una emisión de certificado. Visite el sitio web en un explorador, seleccione el icono de candado y busque una caducidad del certificado. Continúe con [Paso 6](#step-6).\
b. NO - Visita [http://fastly-debug.com](https://www.fastly-debug.com/) y comparte esta información en un [ticket de soporte de Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Paso 6: Confirme que tiene un certificado TSL válido {#step-6}

+++**¿Ha caducado el certificado?**

a. SÍ: debe renovar el certificado TLS con la entidad emisora de certificados (CA).\
b. NO: es posible que no tenga ningún certificado. Si tiene Adobe Commerce, le recomendamos que compre un certificado TLS. Si utiliza Adobe Commerce en una infraestructura en la nube, puede tener un certificado Let&#39;s Encrypt SSL/TLS validado para el dominio para servir tráfico HTTPS seguro desde Fastly. Consulte [proporcionar certificados SSL/TLS](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates) en nuestra documentación para desarrolladores.

+++

[Volver al paso 1](#step-1)
