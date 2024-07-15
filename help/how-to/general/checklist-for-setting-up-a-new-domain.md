---
title: Lista de comprobación para configurar un(a) nuevo(a) [!DNL domain]
description: Esta es una lista de comprobación de cómo configurar un nuevo  [!DNL domain] en Adobe Commerce en la infraestructura en la nube.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: 625ed2c7ab79f7bca9a979903e97c44c875e607c
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# Lista de comprobación para configurar un nuevo(a) [!DNL domain]

Esta es una lista de comprobación de cómo configurar un nuevo(a) [!DNL domain] en Adobe Commerce en la infraestructura en la nube. Se aplica independientemente de si simplemente intenta agregar un nuevo dominio o reemplazar el dominio actual por uno nuevo.

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
