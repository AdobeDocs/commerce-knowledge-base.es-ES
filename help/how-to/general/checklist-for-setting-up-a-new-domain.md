---
title: Lista de comprobación para configurar un(a) nuevo(a) [!DNL domain]
description: Esta es una lista de comprobación de cómo configurar un nuevo  [!DNL domain] en Adobe Commerce en la infraestructura en la nube.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: 552a290b50f9e0c5fa740f26092c57bac447fe68
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 0%

---

# Lista de comprobación para configurar un nuevo(a) [!DNL domain]

Esta lista de comprobación explica cómo configurar un nuevo [!DNL domain] en Adobe Commerce en la infraestructura en la nube. Se aplica tanto si agrega un nuevo dominio como si reemplaza el actual. También se aplica después de obtener un nuevo entorno de ensayo (consulte el paso 4).

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube, [todas las versiones compatibles](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Configuración de un nuevo dominio

>[!NOTE]
>
>Antes de continuar con la configuración del dominio, asegúrese de lo siguiente:
>
>Todas las direcciones URL base están configuradas para utilizar HTTPS en **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**, con el ámbito correcto del sitio web o la vista de tienda.
>> [Forzar TLS](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/redirect-http-to-https-for-all-pages-on-cloud-force-tls#token_type=bearer&expires_in=10799996) está habilitado para redirigir todo el tráfico HTTP a HTTPS en su sitio de Adobe Commerce en la infraestructura en la nube.

### Paso 1: ¿Es esto para [!DNL Integration, Staging] o [!DNL Production environment]?

* **[!DNL Integration]**: [!DNL Custom domains] no son compatibles. Debe usar este método en su lugar: [Configurar varios sitios web o tiendas: Configurar la instalación local](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) en nuestra guía del usuario.
* **[!DNL Staging]**: Vaya a **Paso 2**.
* **[!DNL Production]**: Vaya a **Paso 3**.

### Paso 2 - [!DNL Staging environment]: ¿se encuentra en [!DNL Pro] o en [!DNL Starter]?

* **[!DNL Pro]**: **Envíe una solicitud** para agregar el dominio a [!DNL Fastly, Nginx] y configure [!DNL SSL certificate] (así como [!DNL Sendgrid domain], si es necesario). Una vez que se haya configurado, [actualice la [!DNL DNS] configuración con [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

>[!NOTE]
>
>Para la arquitectura PRO, añadir un nuevo dominio requiere el envío de una solicitud de asistencia a Adobe Commerce. Aunque algunos clientes pueden configurar Fastly manualmente mediante Admin Console, esto solo se aplica en casos limitados, como cuando el dominio no está vinculado a otro servicio o proyecto de Fastly. Sin embargo, la configuración de Nginx siempre es obligatoria, y este paso debe ser gestionado por Adobe. Debido a esto, el enfoque recomendado y más confiable es enviar un [ticket de soporte](https://experienceleague.adobe.com/home?support-tab=home#support) y dejar que Adobe administre todo el proceso de configuración del dominio.


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

### Paso 5: ¿Están configuradas las redirecciones de dominio en `magento-vars.php`?

Una vez configurado el dominio, debe [modificar las variables](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure-store/multiple-sites#modify-variables) en el archivo `magento-vars.php` para dirigir el dominio a la dirección URL del sitio web o tienda correspondiente.

### Paso 6: ¿Se ha verificado la configuración de [!DNL domain]?

Si ha agregado nuevas tiendas, grupos de tiendas y sitios web en **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]** para los nuevos dominios, compruebe si las siguientes secciones aparecen en el archivo `app/etc/config.php`, por ejemplo:

```php
'scopes' => [
    'websites' => [
        'admin' => [
            'website_id' => '0',
            'code' => 'admin',
            'name' => 'Admin',
            'sort_order' => '0',
            'default_group_id' => '0',
            'is_default' => '0',
        ],
        'base' => [
            'website_id' => '1',
            'code' => 'base',
            'name' => 'Main Website',
            'sort_order' => '0',
            'default_group_id' => '1',
            'is_default' => '1',
        ],
        'site2' => [
            'website_id' => '2',
            'code' => 'site2',
            'name' => 'Second Website',
            'sort_order' => '0',
            'default_group_id' => '2',
            'is_default' => '0',
        ],
    ],
    'groups' => [
        0 => [
            'group_id' => '0',
            'website_id' => '0',
            'name' => 'Default',
            'root_category_id' => '0',
            'default_store_id' => '0',
            'code' => 'default',
        ],
        1 => [
            'group_id' => '1',
            'website_id' => '1',
            'name' => 'Main Website Store',
            'root_category_id' => '2',
            'default_store_id' => '1',
            'code' => 'main_website_store',
        ],
        2 => [
            'group_id' => '2',
            'website_id' => '2',
            'name' => 'Second Website Store',
            'root_category_id' => '2',
            'default_store_id' => '2',
            'code' => 'site2store',
        ],
    ],
    'stores' => [
        'admin' => [
            'store_id' => '0',
            'code' => 'admin',
            'website_id' => '0',
            'group_id' => '0',
            'name' => 'Admin',
            'sort_order' => '0',
            'is_active' => '1',
        ],
        'default' => [
            'store_id' => '1',
            'code' => 'default',
            'website_id' => '1',
            'group_id' => '1',
            'name' => 'Default Store View',
            'sort_order' => '0',
            'is_active' => '1',
        ],
        'site2sv' => [
            'store_id' => '2',
            'code' => 'site2sv',
            'website_id' => '2',
            'group_id' => '2',
            'name' => 'Second Website Store view',
            'sort_order' => '0',
            'is_active' => '1',
        ],
    ],
]
```

Esto significa que ya ha configurado [SCD en la compilación](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/deploy/static-content#setting-the-scd-on-build) ejecutando el comando `config:dump` en el paquete `ece-tools`.

Si descubre que el nuevo almacén o sitio web que ha creado no se muestra en el archivo `app/etc/config.php`, asegúrese de ejecutar de nuevo el comando para sincronizar el archivo `config.php` con los cambios realizados en la base de datos, confirme el archivo `config.php` y vuelva a implementar. Esto facilita la implementación de contenido estático para las nuevas tiendas/sitios web en las rutas de archivo adecuadas.

## Lectura relacionada

* [Configurar varios sitios web o tiendas: agregar  [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) nuevos en nuestra guía de usuario.
* [No se puede acceder al sitio debido a la ocultación del origen](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26856)
