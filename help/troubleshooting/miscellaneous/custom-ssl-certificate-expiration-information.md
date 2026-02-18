---
title: Información de caducidad del certificado SSL personalizado
description: Este artículo proporciona una solución para los casos en los que se actualizó un certificado SSL personalizado con un certificado SSL proporcionado por Adobe.
exl-id: cc968bae-f742-449b-b291-bc121ec45935
feature: Support
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Información de caducidad del certificado SSL personalizado

Este artículo proporciona una solución para los casos en los que se actualizó un certificado SSL personalizado con un certificado SSL proporcionado por Adobe.

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube, [todas las versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Adobe Commerce actualiza automáticamente los certificados SSL 30 días antes de la caducidad. Esta automatización no comprueba si el certificado que se reemplaza es un SSL interno o un SSL de terceros personalizado y lo sustituirá por un SSL interno válido al detectar la caducidad. Esto puede causar confusión a los propietarios del sitio y a los operadores que esperan tener el certificado personalizado en el sitio, así como la posibilidad de otros problemas de funcionalidad, incluida, entre otros, una interrupción del sitio.

<u>Pasos a seguir</u>

1. Certificado SSL personalizado instalado para el sitio web.
1. La automatización detecta que el certificado SSL personalizado está a 30 días de caducar.
1. Adobe Commerce reemplaza automáticamente el certificado personalizado por nuestro certificado interno.

<u>Resultados esperados</u>

Adobe Commerce omite los certificados personalizados al ejecutar su actualización de certificados SSL automatizada.

<u>Resultados reales</u>

Adobe Commerce actualiza cualquier certificado cuando quedan 30 días desde la caducidad.

## Solución

Cuando un comerciante decide utilizar su propio certificado SSL personalizado, debe actualizarse más de 30 días antes de la caducidad del certificado para garantizar que no se sustituya por un certificado SSL interno de Adobe Commerce.

Si se encuentra en una situación en la que su SSL personalizado fue reemplazado por nuestro SSL interno y desea reemplazarlo con su certificado SSL personalizado actualizado, [envíe una solicitud de soporte técnico](https://experienceleague.adobe.com/es/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) con la ubicación en la que subió sus nuevos archivos de certificado. Incluya la fecha de inicio del nuevo SSL. Una vez que tengamos esta información, podemos avanzar con la instalación del nuevo certificado SSL.

## Lectura relacionada

* [Certificados SSL (TLS) para Magento Commerce Cloud: preguntas frecuentes](/help/how-to/general/ssl-tls-certificates-for-magento-commerce-cloud-faq.md) en nuestra base de conocimiento de asistencia.
* [Referencia de herramientas de línea de comandos: certificado de Magento en la nube:add](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-reference#certificateadd) en nuestra documentación para desarrolladores.
* [Iniciar lista de comprobación](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/launch/checklist)en nuestra documentación para desarrolladores.
* [Acceda a la herramienta de análisis de todo el sitio](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/site-wide-analysis-tool/access#step-2-access-site-wide-analysis-tool) en nuestra guía del usuario.
