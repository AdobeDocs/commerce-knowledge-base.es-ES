---
title: "Error 60 de cURL: certificado SSL caducado"
description: '"Este artículo muestra cómo comprobar cuándo se implementó una rama por última vez después de recibir un error cURL 60: El certificado SSL caducó en las ramas maestra o de integración en Adobe Commerce en la infraestructura en la nube".'
exl-id: 74f1db7e-ee2b-4e27-8fcc-fe462a9e72c3
feature: Configuration
role: Developer
source-git-commit: 6f631ca35b663c386bca9efe6e56db266502c0b1
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# Error 60 de cURL: certificado SSL caducado

Este artículo muestra cómo comprobar cuándo se implementó una rama por última vez después de recibir una `cURL error 60`: [!DNL SSL certificate] caducado en el [!DNL Master] o [!DNL Integration] ramas de Adobe Commerce en la infraestructura en la nube.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, [todas las versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Causa

El [!DNL SSL certificates] en esas ramas sólo son válidas durante 30 días, y es posible que la rama no se haya redesplegado en más de 30 días.

El error será similar al siguiente:

```cURL
cURL error 60: SSL certificate problem: certificate has expired
```

## Solución

Compruebe cuándo se implementó la rama por última vez. Si supera el umbral de 30 días, vuelva a implementar la rama.

Dos métodos para comprobar cuándo se realizó la última implementación:

* [Método 1: Uso [!DNL magento-cloud] CLI](#meth2).
* [Método 2: Abrir [!DNL Project URL]](#meth3).

Si la implementación se ha completado correctamente, la variable [!DNL SSL certificate] se renovará automáticamente.

Si la implementación falla y necesita ayuda para resolverla, [enviar un ticket de asistencia](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

### Método 1: Uso [!DNL magento-cloud] CLI {#meth2}

Ejecute este comando: `magento-cloud activity:list`

### Método 2: Abrir [!DNL Project URL] {#meth3}

Vaya a, por ejemplo: `https://demo.magento.cloud/#/projects/<project>/environments/<environment>`y compruebe cuándo se realizó la última implementación.

## Lectura relacionada

En nuestra documentación para desarrolladores:

* [API de Cloud Manager: Certificados SSL](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/SSLCertificates)
* [Configuración rápida: Aprovisionar certificados SSL/TLS](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#provision-ssltls-certificates)

En nuestra base de conocimiento de soporte:

* [Información de caducidad del certificado SSL personalizado](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/custom-ssl-certificate-expiration-information.html)
* [Certificados SSL (TLS) para Adobe Commerce en infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/ssl-tls-certificates-for-magento-commerce-cloud-faq.html)
