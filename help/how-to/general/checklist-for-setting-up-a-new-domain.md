---
title: Lista de comprobación para configurar un(a) nuevo(a) [!DNL domain]
description: Esta es una lista de comprobación de cómo configurar un nuevo  [!DNL domain] en Adobe Commerce en la infraestructura en la nube.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: f7b246088e3580922bd3389b2992e5dd8f97ff7a
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Lista de comprobación para configurar un nuevo(a) [!DNL domain]

Esta lista de comprobación explica cómo configurar un nuevo [!DNL domain] en Adobe Commerce en la infraestructura en la nube. Se aplica tanto si agrega un nuevo dominio como si reemplaza el actual. También se aplica después de obtener un nuevo entorno de ensayo (consulte el paso 4).

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube, [todas las versiones compatibles](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Configuración de un nuevo dominio

### Paso 1: ¿Es esto para [!DNL Integration, Staging] o [!DNL Production environment]?

* **[!DNL Integration]**: [!DNL Custom domains] no son compatibles. Debe usar este método en su lugar: [Configurar varios sitios web o tiendas: Configurar la instalación local](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) en nuestra guía del usuario.
* **[!DNL Staging]**: Vaya a **Paso 2**.
* **[!DNL Production]**: Vaya a **Paso 3**.

### Paso 2 - [!DNL Staging environment]: ¿se encuentra en [!DNL Pro] o en [!DNL Starter]?

* **[!DNL Pro]**: **Envíe una solicitud** para agregar el dominio a [!DNL Fastly, Nginx] y configure [!DNL SSL certificate] (así como [!DNL Sendgrid domain], si es necesario). Una vez que se haya configurado, [actualice la [!DNL DNS] configuración con [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

>[!NOTE]
>
>Puede agregar el nuevo(a) [!DNL domain] a [!DNL Fastly] usted mismo al actualizar la configuración en [!DNL Admin] en **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** como en [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) en nuestra guía del usuario.
>
>Si no puede agregar el dominio, puede deberse a uno de los siguientes motivos:
>
>1. Está migrando el dominio al entorno de nube, que se ha configurado en su propio servicio [!DNL Fastly]. En este caso, envíe una solicitud y solicite la delegación del dominio.
>1. Está migrando el dominio de Starter a Pro. En este caso, envíe una solicitud de asistencia adicional.

* **[!DNL Starter]**: [!DNL Custom domains] no son compatibles con el entorno de ensayo.

### Paso 3 - [!DNL Production environment]: ¿se encuentra en [!DNL Pro] o en [!DNL Starter]?

* **[!DNL Pro]**: **Envíe una solicitud** para agregar el dominio a [!DNL Fastly, Nginx] y configure [!DNL SSL certificate] (como [!DNL Sendgrid domain], si es necesario). Una vez que se haya configurado, continúe con **Paso 4**.

>[!NOTE]
>
>Puede agregar el nuevo(a) [!DNL domain] a [!DNL Fastly] usted mismo al actualizar la configuración en [!DNL Admin] en **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) en nuestra guía del usuario.
>
>
>Si no puede agregar el dominio, puede deberse a uno de los siguientes motivos:
>
>1. Está migrando el dominio de local a entorno de nube, que se ha configurado en su propio servicio [!DNL Fastly]. En este caso, envíe una solicitud y solicite la delegación del dominio.
>1. Está migrando el dominio de Starter a Pro. En este caso, envíe una solicitud de asistencia adicional.

* **[!DNL Starter]**: Agregue [!DNL domain] a su proyecto en la ficha **[!DNL Domains]** y después **envíe una solicitud** para proporcionar **[!DNL ACME Challenge Key]** para [!DNL SSL certificate].

### Paso 4: ¿Está activo [!DNL domain]?

* **SÍ**: [Actualice la configuración [!DNL DNS] con la configuración [!UICONTROL production]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html#update-dns-configuration-with-production-settings).
* **NO**: [Actualice la [!DNL DNS] configuración con [!UICONTROL development] configuración](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

## Lectura relacionada

* [Configurar varios sitios web o tiendas: agregar  [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) nuevos en nuestra guía de usuario.
* [No se puede acceder al sitio debido a la ocultación del origen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/production-site-not-accessible-due-to-origin-cloaking)
