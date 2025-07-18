---
title: 'Error 60 de cURL: certificado SSL caducado'
description: 'Este artículo muestra cómo comprobar cuándo se implementó una rama por última vez después de recibir un error cURL 60: El certificado SSL caducó en las ramas Master o Integration en Adobe Commerce en la infraestructura en la nube.'
exl-id: 74f1db7e-ee2b-4e27-8fcc-fe462a9e72c3
feature: Configuration
role: Developer
source-git-commit: dcaae51408534b82181b268f60905b123e240900
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Error 60 de cURL: certificado SSL caducado

Este artículo muestra cómo comprobar cuándo se implementó una rama por última vez después de recibir `cURL error 60`: [!DNL SSL certificate] caducó en las ramas [!DNL Master] o [!DNL Integration] en Adobe Commerce en la infraestructura en la nube.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, [todas las versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Causa

Las [!DNL SSL certificates] de esas ramas solo son válidas durante 30 días, y es posible que la rama no se haya vuelto a implementar en más de 30 días.

El error será similar al siguiente:

```cURL
cURL error 60: SSL certificate problem: certificate has expired
```

>[!NOTE]
>
>Estos certificados no están firmados por entidades de certificación (CA) externas conocidas como [!DNL Let's Encrypt] o [!DNL DigiCert]. La plataforma Adobe los administra con fines de prueba y desarrollo y es posible que no se confíe en ellos de forma predeterminada en los exploradores o curl a menos que confíe explícitamente en la raíz que emite el certificado.

## Solución

Compruebe cuándo se implementó la rama por última vez. Si supera el umbral de 30 días, vuelva a implementar la rama.

Dos métodos para comprobar cuándo se realizó la última implementación:

* [Método 1: usar [!DNL magento-cloud] CLI](#meth2).
* [Método 2: abrir [!DNL Project URL]](#meth3).

Si la implementación se completó correctamente, [!DNL SSL certificate] se renovará automáticamente.

Si la implementación falla y necesita ayuda para resolverla, [envíe un vale de soporte técnico](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=es#submit-ticket).

### Método 1: usar CLI [!DNL magento-cloud] {#meth2}

Ejecutar este comando: `magento-cloud activity:list --type=environment.push`

### Método 2: abrir [!DNL Project URL] {#meth3}

Vaya a, por ejemplo: `https://demo.magento.cloud/#/projects/<project>/environments/<environment>`, y compruebe cuándo se realizó la última implementación.

## Lectura relacionada

En nuestra documentación para desarrolladores:

* [API de Cloud Manager: SSLCertificates](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/SSLCertificates)
* [Configurar rápidamente: aprovisionar certificados SSL/TLS](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates)

En nuestra base de conocimiento de soporte:

* [Información de caducidad del certificado SSL personalizado](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/custom-ssl-certificate-expiration-information.html?lang=es)
* [Certificados SSL (TLS) para Adobe Commerce en la infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/ssl-tls-certificates-for-magento-commerce-cloud-faq.html?lang=es)
