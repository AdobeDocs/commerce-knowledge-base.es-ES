---
title: Certificados SSL (TLS) para Adobe Commerce en infraestructura en la nube
description: Este artículo proporciona respuestas rápidas a preguntas sobre cómo obtener certificados SSL (TLS) para su sitio de Adobe Commerce en nuestra infraestructura de nube.
exl-id: 5a682d07-e4d7-4e81-a2ad-3232f2d8d9c1
feature: Cloud, Console
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '1090'
ht-degree: 0%

---

# Certificados SSL (TLS) para Adobe Commerce en infraestructura en la nube

Este artículo proporciona respuestas rápidas a preguntas sobre cómo obtener certificados SSL (TLS) para su sitio de Adobe Commerce en nuestra infraestructura de nube.

## ¿Qué certificado SSL/TLS proporciona Adobe?

Adobe proporciona un certificado [Let&#39;s Encrypt SSL/TLS](https://letsencrypt.org/) validado para el dominio para servir tráfico HTTPS seguro desde [!DNL Fastly]. Adobe proporciona un certificado para cada Adobe Commerce en la infraestructura en la nube, arquitectura de plan Pro, ensayo y Adobe Commerce en la infraestructura en la nube, el entorno de arquitectura de plan inicial para proteger todos los dominios de ese entorno.

## ¿Qué cubre un certificado?

Para la arquitectura de plan Pro, los entornos dedicados de Ensayo y Producción tendrán un certificado SSL creado. Cada entorno dedicado fuera de los entornos de integración de plataforma como servicio (PaaS) tendrá este certificado para las URL asignadas a ese entorno.

Para la arquitectura del plan de inicio y los entornos de integración de PaaS, habrá un dominio técnico predeterminado que se aprovisionará con el entorno y se protegerá con un certificado independiente.

## ¿Cómo se agrega un nuevo dominio para el certificado existente?

Para agregar el dominio al servicio en [!DNL Fastly]:

1. Dirija su dominio en DNS a prod.magentocloud.map.fastly.net y espere hasta 6 horas.
1. [Envíe un ticket de asistencia](https://experienceleague.adobe.com/es/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) solicitando agregar este dominio en la configuración de Nginx (si no lo ha hecho antes).

## ¿Cómo se solicita un certificado?

Caso 1

Si todavía no ha lanzado un sitio web, es posible que haya recibido el CNAME del desafío ACME de su asesor técnico de cliente (CTA). Solo necesita un desafío ACME si no puede apuntar inmediatamente su DNS a la URL de producción y necesita obtener los certificados SSL creados por adelantado.

Caso 2

Si su sitio ya está activo o puede señalar las direcciones URL que se utilizarán para su sitio activo de inmediato, no necesita solicitar un CNAME de ACME. Una vez que agregue las direcciones URL según sea necesario a su sitio de infraestructura de Adobe Commerce en la nube y señale su DNS a [!DNL Fastly], la validación HTTP funcionará y creará su certificado SSL por primera vez o lo actualizará con direcciones URL adicionales.

## ¿Puedo utilizar mi propio certificado SSL/TLS?

Puede proporcionar su propio certificado SSL/TLS en lugar de usar el [certificado Let&#39;s Encrypt](https://letsencrypt.org/) proporcionado por Adobe.

Sin embargo, este proceso requiere un trabajo adicional de configuración y mantenimiento. En primer lugar, deberá generar una Solicitud de firma de certificado (CSR) para el nombre de dominio del sitio web (o nombre común) y proporcionárselo a su proveedor SSL para proporcionar un certificado SSL.

Una vez que tenga el certificado SSL, envíe un [vale de soporte de Adobe Commerce](https://experienceleague.adobe.com/es/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) o trabaje con su CTA para agregar certificados alojados personalizados a sus entornos de nube.

* Si los dominios ya no están en uso, se eliminarán automáticamente de nuestro sistema y no se requiere ninguna acción adicional.
* Si ya posee un certificado, cárguelo a través de un cliente SFTP (SSH File Transfer Protocol) en una ubicación de archivo no accesible en la web de su servidor y [envíe un ticket de asistencia](https://experienceleague.adobe.com/es/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) para que sepan la ruta del archivo.

>[!WARNING]
>
>Es importante que no cargue los archivos de certificado directamente en el ticket. De lo contrario, los certificados se considerarán comprometidos y Adobe deberá solicitar un nuevo certificado.
>Los archivos deben cargarse mediante SFTP al servidor en una carpeta de su elección, por ejemplo: `var/ssl`, `/tmp/ssl`, etc. : no utilice ningún otro método como confirmar los archivos en el repositorio (lo que solo debe hacerse para archivos inmutables que no contengan datos confidenciales).

## El nombre del certificado

El nombre del certificado SSL solo importa para la URL principal, y es el nombre de host principal denominado por la primera URL y debe coincidir para que se valide y cree. Si tiene algunas direcciones URL, se agregarán como entradas de nombre alternativo del sujeto al certificado. Si tiene varias direcciones URL que apuntan a un sitio de Adobe Commerce en la infraestructura de la nube, solo tendrá un certificado de URL de nombre común que tendrá nombres alternativos del sujeto añadidos para proteger el sitio con SSL.

## ¿Qué dominio se mostrará en el campo Nombre común del certificado?

El dominio mostrado en el certificado es solo el primer dominio agregado al certificado TLS, rellena el campo **Nombre común** (**CN**) y los exploradores muestran primero este nombre. El campo **Nombre alternativo del sujeto** (**SAN**) contiene todos los nombres DNS para el certificado TLS. No hay forma de cambiar o solicitar el Nombre común que se muestra.

## ¿Puedo utilizar certificados TLS comodín?

Los certificados TLS comodín solo se pueden usar con el certificado personalizado y no con los certificados de Adobe Commerce Let&#39;s Encrypt. Como parte de la optimización de TLS, Adobe va a dejar de ofrecer soporte para los certificados TLS comodín. Estamos identificando y poniéndonos en contacto con comerciantes que utilizan un certificado comodín con los certificados Let&#39;s Encrypt de Adobe y que están configurados en la consola [!DNL Fastly] para Adobe Commerce. Pedimos que estos certificados comodín se sustituyan por dominios exactos para garantizar la cobertura TLS. Para reemplazar un certificado TLS comodín, visite la [sección de dominio](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration#manage-domains) del complemento [!DNL Fastly]. Desde aquí, se pueden añadir los dominios exactos y se puede eliminar el comodín. Tenga en cuenta que DNS tendrá que señalar a [!DNL Fastly] para que estos nuevos dominios se enruten a través de la CDN. Una vez que se agreguen los dominios y se actualice el DNS, se proporcionará un certificado [Let&#39;s Encrypt](https://letsencrypt.org/) coincidente. Si no quita un dominio que señala a [!DNL Fastly] mediante un comodín, Adobe eliminará el certificado compartido. Esto puede provocar una interrupción del sitio si no tiene configurado el FQDN de la dirección URL y el mismo FQDN de la dirección URL configurado en el DNS. Por lo tanto, debe confirmar que las direcciones URL configuradas también tienen una coincidencia uno a uno en su DNS que señala a [!DNL Fastly].

## ¿Qué debo hacer si mi dominio ya no apunta a Adobe Commerce?

Si su dominio ya no apunta a Adobe Commerce, elimínelo del sistema [!DNL Fastly]/Adobe Commerce. Vea [!DNL Fastly] [Eliminando un dominio](https://docs.fastly.com/en/guides/working-with-domains#deleting-a-domain) para obtener más información. Aunque no es necesario apuntar el dominio a Adobe Commerce, confirme si se requiere un certificado TLS de dominio de nivel superior. Si se requiere un dominio de nivel superior, actualice su DNS para que apunte a Adobe Commerce. Si ya apunta a Adobe Commerce, actualice el registro de CA para que incluya [lets-encrypt](https://letsencrypt.org/). Si realiza estos pasos, verá el certificado LE actualizado con las direcciones URL secundarias necesarias que cubre el certificado&#x200B;

## Lectura relacionada

[Proporcionar certificados SSL/TLS](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates) en nuestra documentación para desarrolladores
