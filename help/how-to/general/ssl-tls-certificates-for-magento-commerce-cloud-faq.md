---
title: Certificados SSL (TLS) para Adobe Commerce en infraestructura en la nube
description: Este artículo proporciona respuestas rápidas a preguntas sobre cómo obtener certificados SSL (TLS) para su sitio de Adobe Commerce en nuestra infraestructura de nube.
exl-id: 5a682d07-e4d7-4e81-a2ad-3232f2d8d9c1
feature: Cloud, Console
source-git-commit: 43c3e5f95c4b54e235140cd5b3978d3887af5ee1
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 0%

---

# Certificados SSL (TLS) para Adobe Commerce en infraestructura en la nube

Este artículo proporciona respuestas rápidas a preguntas sobre cómo obtener certificados SSL (TLS) para su sitio de Adobe Commerce en nuestra infraestructura de nube.

## ¿Qué certificado SSL/TLS proporciona el Adobe?

El Adobe proporciona un dominio validado [Vamos a codificar el certificado SSL/TLS](https://letsencrypt.org/) para proporcionar tráfico HTTPS seguro desde [!DNL Fastly]. Adobe proporciona un certificado para cada Adobe Commerce en la infraestructura en la nube, arquitectura de plan Pro, ensayo y Adobe Commerce en la infraestructura en la nube, el entorno de arquitectura de plan inicial para proteger todos los dominios de ese entorno.

## ¿Qué cubre un certificado?

Para la arquitectura de plan Pro, los entornos dedicados de Ensayo y Producción tendrán un certificado SSL creado. Cada entorno dedicado fuera de los entornos de integración de plataforma como servicio (PaaS) tendrá este certificado para las URL asignadas a ese entorno.

Para la arquitectura del plan de inicio y los entornos de integración de PaaS, habrá un dominio técnico predeterminado que se aprovisionará con el entorno y se protegerá con un certificado independiente.

## ¿Cómo se agrega un nuevo dominio para el certificado existente?

Para agregar el dominio al servicio en [!DNL Fastly]:

1. Dirija su dominio en DNS a prod.magentocloud.map.fastly.net y espere hasta 6 horas.
1. [Enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) solicitando agregar este dominio en la configuración de Nginx (si no lo ha hecho anteriormente).

## ¿Cómo se solicita un certificado?

Caso 1

Si todavía no ha lanzado un sitio web, es posible que haya recibido el CNAME del desafío ACME de su asesor técnico de cliente (CTA). Solo necesita un desafío ACME si no puede apuntar inmediatamente su DNS a la URL de producción y necesita obtener los certificados SSL creados por adelantado.

Caso 2

Si su sitio ya está activo o puede señalar las direcciones URL que se utilizarán para su sitio activo de inmediato, no necesita solicitar un CNAME de ACME. Una vez que añada las direcciones URL necesarias a su sitio de Adobe Commerce en la infraestructura de la nube y señale su DNS a [!DNL Fastly], la validación HTTP funcionará y creará su certificado SSL por primera vez o actualizará su certificado con direcciones URL adicionales.

## ¿Puedo utilizar mi propio certificado SSL/TLS?

Puede proporcionar su propio certificado SSL/TLS en lugar de utilizar el [Vamos a cifrar el certificado](https://letsencrypt.org/) proporcionadas por el Adobe.

Sin embargo, este proceso requiere un trabajo adicional de configuración y mantenimiento. En primer lugar, deberá generar una Solicitud de firma de certificado (CSR) para el nombre de dominio del sitio web (o nombre común) y proporcionárselo a su proveedor SSL para proporcionar un certificado SSL.

Una vez que tenga el certificado SSL, envíe un [ticket de asistencia de Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) o trabaje con su CTA para agregar certificados alojados personalizados a sus entornos de nube.

* Si los dominios ya no están en uso, se eliminarán automáticamente de nuestro sistema y no se requiere ninguna acción adicional.
* Si ya tiene un certificado, cárguelo mediante un cliente SFTP (SSH File Transfer Protocol) en una ubicación de archivos no accesibles en la web en su servidor y [enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para que conozcan la ruta del archivo.

>[!WARNING]
>
>Es importante que no cargue los archivos de certificado directamente en el ticket. De lo contrario, los certificados se considerarán comprometidos y el Adobe deberá solicitar un nuevo certificado.
>Los archivos deben cargarse mediante SFTP al servidor. No utilice ningún otro método, como enviar los archivos al repositorio (lo cual solo debe hacerse para archivos inmutables que no contengan datos confidenciales).

## El nombre del certificado

El nombre del certificado SSL solo importa para la URL principal, y es el nombre de host principal denominado por la primera URL y debe coincidir para que se valide y cree. Si tiene algunas direcciones URL, se agregarán como entradas de nombre alternativo del sujeto al certificado. Si tiene varias direcciones URL que apuntan a un sitio de Adobe Commerce en la infraestructura de la nube, solo tendrá un certificado de URL de nombre común que tendrá nombres alternativos del sujeto añadidos para proteger el sitio con SSL.

## ¿Qué dominio se mostrará en el campo Nombre común del certificado?

El dominio mostrado en el certificado es solo el primer dominio agregado al certificado TLS, rellena el **Nombre común** (**CN**) y los exploradores muestran primero este nombre. El **Nombre alternativo del sujeto** (**SAN**) contiene todos los nombres DNS para el certificado TLS. No hay forma de cambiar o solicitar el Nombre común que se muestra.

## ¿Puedo utilizar certificados TLS comodín?

Los certificados TLS comodín solo se pueden usar con el certificado personalizado y no con los certificados de Adobe Commerce Let&#39;s Encrypt. Como parte de la optimización de TLS, el Adobe va a dejar de ofrecer compatibilidad con certificados TLS comodín. Estamos identificando y poniéndonos en contacto con comerciantes que utilizan un certificado comodín con los certificados Let&#39;s Encrypt de Adobe y que están configurados en la [!DNL Fastly] para Adobe Commerce. Pedimos que estos certificados comodín se sustituyan por dominios exactos para garantizar la cobertura TLS. Para reemplazar un certificado TLS comodín, visite el [sección de dominio](https://devdocs.magento.com/cloud/cdn/configure-fastly-customize-cache.html#manage-domains) de la [!DNL Fastly] plugin. Desde aquí, se pueden añadir los dominios exactos y se puede eliminar el comodín. Tenga en cuenta que el DNS tendrá que señalar a [!DNL Fastly] para que estos nuevos dominios enruten a través de la CDN. Una vez agregados los dominios y actualizado el DNS, se muestra una [Vamos a codificar](https://letsencrypt.org/) se proporcionará el certificado. Si no quita un dominio que señala a [!DNL Fastly] con un comodín, el Adobe eliminará el certificado compartido. Esto puede provocar una interrupción del sitio si no tiene configurado el FQDN de la dirección URL y el mismo FQDN de la dirección URL configurado en el DNS. Por lo tanto, debe confirmar que las direcciones URL configuradas también tienen una coincidencia uno a uno en su DNS que señala a [!DNL Fastly].

## ¿Qué debo hacer si mi dominio ya no apunta a Adobe Commerce?

Si su dominio ya no apunta a Adobe Commerce, elimínelo del [!DNL Fastly]/Adobe Commerce sistema. Consulte [!DNL Fastly] [Eliminación de un dominio](https://docs.fastly.com/en/guides/working-with-domains#deleting-a-domain) para obtener más información. Aunque no es necesario apuntar el dominio a Adobe Commerce, confirme si se requiere un certificado TLS de dominio de nivel superior. Si se requiere un dominio de nivel superior, actualice su DNS para que apunte a Adobe Commerce. Si ya apunta a Adobe Commerce, actualice el registro de CA para que incluya [let-encrypt](https://letsencrypt.org/). Si realiza estos pasos, verá el certificado LE actualizado con las direcciones URL secundarias necesarias que cubre el certificado&#x200B;

## Lectura relacionada

[Aprovisionar certificados SSL/TLS](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#provision-ssltls-certificates) en nuestra documentación para desarrolladores
