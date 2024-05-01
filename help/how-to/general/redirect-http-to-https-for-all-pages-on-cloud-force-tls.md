---
title: Redirigir HTTP a HTTPS para todas las páginas en Adobe Commerce en la infraestructura en la nube (Forzar TLS)
description: Active la funcionalidad **Force TLS** de Fastly en el administrador de Commerce para habilitar el redireccionamiento de HTTP a HTTPS global para todas las páginas de su Adobe Commerce en el almacén de infraestructura de la nube.
exl-id: 71667f52-a99a-47a6-99d8-10532364870f
feature: Cache, Cloud
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Redirigir HTTP a HTTPS para todas las páginas en Adobe Commerce en la infraestructura en la nube (Forzar TLS)

Activar el de Fastly **Forzar TLS** en el administrador de Commerce para habilitar el redireccionamiento global HTTP a HTTPS para todas las páginas de su Adobe Commerce en el almacén de infraestructura en la nube.

Este artículo proporciona información detallada [pasos](#steps), una breve descripción general de la función Force TLS, las versiones afectadas y los vínculos a la documentación relacionada.

## Pasos {#steps}

### Paso 1: Configurar direcciones URL seguras {#step-1-configure-secure-urls}

En este paso, definimos las direcciones URL seguras para la tienda. Si ya lo ha hecho, vaya a [Paso 2: Habilitar Force TLS](#step-2-enable-force-tls).

1. Inicie sesión en el administrador de Commerce.
1. Vaya a **Tiendas** > **Configuración** > **General** > **Web**.
1. Expanda el **URL básicas (seguras)** sección.    ![magento-admin_base-urls-secure.png](assets/magento-admin_base-urls-secure.png)
1. En el **URL base segura** , especifique la URL HTTPS de la tienda.
1. Configure las variables **Usar URL seguras en tienda** y el **Usar URL seguras en el administrador** configuración para **Sí**.    ![magento-admin_base-urls-secure-settings.png](assets/magento-admin_base-urls-secure-settings.png)
1. Clic **Guardar configuración** en la esquina superior derecha para aplicar los cambios.

**Documentación relacionada en nuestra guía de usuario:**   [URL de tienda](https://docs.magento.com/m2/ee/user_guide/stores/store-urls.html).

### Paso 2: Habilitar Force TLS {#step-2-enable-force-tls}

1. En el Administrador de Commerce, vaya a **Tiendas** > **Configuración** > **Avanzadas** > **Sistema**.
1. Expanda el **Caché de página completa** , entonces **Configuración rápida**, entonces **Configuración avanzada**.
1. Haga clic en **Forzar TLS** botón.    ![magento-admin_force-tls-button.png](assets/magento-admin_force-tls-button.png)
1. En el cuadro de diálogo que aparece, haga clic en **Cargar**.    ![magento-admin_force-tls-confirmation-dialog.png](assets/magento-admin_force-tls-confirmation-dialog.png)
1. Una vez cerrado el cuadro de diálogo, asegúrese de que el estado actual de Forzar TLS se muestre como **activado**.    ![magento-admin_force-tls-enabled.png](assets/magento-admin_force-tls-enabled.png)

**Documentación relacionada de Fastly:**   [Forzar guía TLS](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/FORCE-TLS.md) para Adobe Commerce 2.

## Acerca de Forzar TLS

TLS (Transport Layer Security) es un protocolo para conexiones HTTP seguras que reemplaza a su predecesor menos seguro: el protocolo SSL (Secure Socket Layer).

La funcionalidad Force TLS de Fastly le permite forzar todas las solicitudes entrantes sin cifrar para las páginas del sitio a TLS.

>>
Funciona devolviendo un *301 movido permanentemente* respuesta a cualquier solicitud no cifrada, que redirige al equivalente TLS. Por ejemplo, realizar una solicitud de *http://www.example.com/foo.jpeg* se redirigiría a *https://www.example.com/foo.jpeg*.

[Proteger comunicaciones](https://docs.fastly.com/guides/securing-communications/) (Documentación de Fastly)

## Versiones afectadas

* **Adobe Commerce en la infraestructura en la nube:**
   * versión: 2.1.4 y posterior
   * planes: Adobe Commerce en la infraestructura en la nube Arquitectura del plan inicial y Adobe Commerce en la infraestructura en la nube Arquitectura del plan Pro (incluido el programa heredado Pro)
* **Rápidamente:** 1.2.4

## No se necesitan cambios en routes.yaml

Para habilitar el redireccionamiento de HTTP a HTTPS en **todo** páginas de su tienda, no tiene que añadir las páginas a la `routes.yaml` archivo de configuración: habilitar Force TLS globalmente para todo el almacén (con el administrador de Commerce) es suficiente.

## Documentación de Fastly relacionada

* [Forzar guía TLS para Adobe Commerce 2](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/FORCE-TLS.md)
* [Forzar una redirección TLS](https://docs.fastly.com/guides/securing-communications/forcing-a-tls-redirect)
* [Proteger comunicaciones](https://docs.fastly.com/guides/securing-communications/)
