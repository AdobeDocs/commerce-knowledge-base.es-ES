---
title: Lista de comprobación para configurar una nueva [!DNL domain]
description: Esta es una lista de comprobación de cómo configurar un nuevo [!DNL domain] en Adobe Commerce sobre la infraestructura en la nube.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: 625ed2c7ab79f7bca9a979903e97c44c875e607c
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# Lista de comprobación para configurar una nueva [!DNL domain]

Esta es una lista de comprobación de cómo configurar un nuevo [!DNL domain] en Adobe Commerce sobre la infraestructura en la nube. Se aplica independientemente de si simplemente intenta agregar un nuevo dominio o reemplazar el dominio actual por uno nuevo.

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube, [todas las versiones compatibles](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Configuración de un nuevo dominio

### Paso 1: ¿Es esto para? [!DNL Integration, Staging], o [!DNL Production environment]?

* **[!DNL Integration]**: [!DNL Custom domains] no son compatibles. Debe utilizar este método en su lugar: [Configurar varios sitios web o tiendas: configurar la instalación local](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) en nuestra guía del usuario.
* **[!DNL Staging]**: Vaya a **Paso 2**.
* **[!DNL Production]**: Vaya a **Paso 3**.

### Paso 2: [!DNL Staging environment]: ¿está usted en [!DNL Pro] o [!DNL Starter]?

* **[!DNL Pro]**: **Envío de una solicitud** para agregar el dominio a [!DNL Fastly, Nginx]y configure el [!DNL SSL certificate] (así como el [!DNL Sendgrid domain], si es necesario). Una vez que se haya configurado, [actualice el [!DNL DNS] configuración con [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

>[!NOTE]
>
>Puede añadir el nuevo [!DNL domain] hasta [!DNL Fastly] Actualice la configuración en el [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** como en [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) en nuestra guía del usuario.
>
>Si no puede agregar el dominio, puede deberse a uno de los siguientes motivos:
>
>1. Está migrando el dominio al entorno de nube, que se ha configurado en el suyo propio [!DNL Fastly] servicio. En este caso, envíe una solicitud y solicite la delegación del dominio.
>1. Está migrando el dominio de Starter a Pro. En este caso, envíe una solicitud de asistencia adicional.

* **[!DNL Starter]**: [!DNL Custom domains] no son compatibles con el entorno de ensayo.

### Paso 3: [!DNL Production environment]: ¿está usted en [!DNL Pro] o [!DNL Starter]?

* **[!DNL Pro]**: **Envío de una solicitud** para agregar el dominio a [!DNL Fastly, Nginx]y configure el [!DNL SSL certificate] (como el [!DNL Sendgrid domain], si es necesario). Una vez que se haya configurado, continúe con **Paso 4**.

>[!NOTE]
>
>Puede añadir el nuevo [!DNL domain] hasta [!DNL Fastly] Actualice la configuración en el [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) en nuestra guía del usuario.
>
>
>Si no puede agregar el dominio, puede deberse a uno de los siguientes motivos:
>
>1. Está migrando el dominio de local a entorno de nube, que se ha configurado en su propio [!DNL Fastly] servicio. En este caso, envíe una solicitud y solicite la delegación del dominio.
>1. Está migrando el dominio de Starter a Pro. En este caso, envíe una solicitud de asistencia adicional.

* **[!DNL Starter]**: Añada el [!DNL domain] al proyecto en el **[!DNL Domains]** pestaña, luego **enviar una solicitud** para proporcionar el **[!DNL ACME Challenge Key]** para el [!DNL SSL certificate].

### Paso 4: ¿La variable [!DNL domain] ¿vivir?

* **SÍ**: [Actualice el [!DNL DNS] configuración con [!UICONTROL production] configuración](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html#update-dns-configuration-with-production-settings).
* **NO**: [Actualice el [!DNL DNS] configuración con [!UICONTROL development] configuración](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

## Lectura relacionada

* [Configurar varios sitios web o tiendas: Agregar nuevo [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) en nuestra guía del usuario.
