---
title: Redirigir HTTP a HTTPS para todas las páginas en Adobe Commerce en la infraestructura en la nube (Forzar TLS)
description: Active la funcionalidad **Force TLS** de Fastly en el administrador de Commerce para habilitar el redireccionamiento de HTTP a HTTPS global para todas las páginas de su Adobe Commerce en el almacén de infraestructura de la nube.
exl-id: 71667f52-a99a-47a6-99d8-10532364870f
feature: Cache, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Redirigir HTTP a HTTPS para todas las páginas en Adobe Commerce en la infraestructura en la nube (Forzar TLS)

Active la funcionalidad **Forzar TLS** de Fastly en el administrador de Commerce para habilitar el redireccionamiento de HTTP global a HTTPS para todas las páginas de su Adobe Commerce en el almacén de infraestructura de nube.

Este artículo incluye [pasos](#steps) detallados, una descripción general rápida de la función Forzar TLS, versiones afectadas y vínculos a documentación relacionada.

## Pasos {#steps}

### Paso 1: Configurar direcciones URL seguras {#step-1-configure-secure-urls}

En este paso, definimos las direcciones URL seguras para la tienda. Si ya lo ha hecho, vaya a [Paso 2: Habilitar Forzar TLS](#step-2-enable-force-tls).

1. Inicie sesión en el administrador de Commerce.
1. Vaya a **Tiendas** > **Configuración** > **General** > **Web**.
1. Expanda la sección **URL básicas (seguras)**.    ![magento-admin_base-urls-secure.png](assets/magento-admin_base-urls-secure.png)
1. En el campo **URL base segura**, especifique la URL HTTPS de su tienda.
1. Establece la configuración **Usar direcciones URL seguras en tienda** y **Usar direcciones URL seguras en administración** en **Sí**.    ![magento-admin_base-urls-secure-settings.png](assets/magento-admin_base-urls-secure-settings.png)
1. Haga clic en **Guardar configuración** en la esquina superior derecha para aplicar los cambios.

**Documentación relacionada en nuestra guía del usuario:**   [URL de la tienda](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/store-urls).

### Paso 2: Habilitar Force TLS {#step-2-enable-force-tls}

1. En el Administrador de Commerce, vaya a **Tiendas** > **Configuración** > **Avanzado** > **Sistema**.
1. Expanda la sección **Caché de página completa**, después **Configuración rápida** y después **Configuración avanzada**.
1. Haga clic en el botón **Forzar TLS**.    ![magento-admin_force-tls-button.png](assets/magento-admin_force-tls-button.png)
1. En el cuadro de diálogo que aparece, haga clic en **Cargar**.    ![magento-admin_force-tls-confirmation-dialog.png](assets/magento-admin_force-tls-confirmation-dialog.png)
1. Una vez cerrado el cuadro de diálogo, asegúrese de que el estado actual de Forzar TLS se muestre como **habilitado**.    ![magento-admin_force-tls-enabled.png](assets/magento-admin_force-tls-enabled.png)

**Documentación relacionada de Fastly:**   [Forzar guía TLS](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/FORCE-TLS.md) para Adobe Commerce 2.

## Acerca de Forzar TLS

TLS (Transport Layer Security) es un protocolo para conexiones HTTP seguras que reemplaza a su predecesor menos seguro: el protocolo SSL (Secure Socket Layer).

La funcionalidad Force TLS de Fastly le permite forzar todas las solicitudes entrantes sin cifrar para las páginas del sitio a TLS.

&#x200B;>>
Funciona devolviendo una respuesta *301 movida permanentemente* a cualquier solicitud no cifrada, que redirige al equivalente TLS. Por ejemplo, hacer una solicitud para *http://www.example.com/foo.jpeg* redirigiría a *https://www.example.com/foo.jpeg*.

[Protección de las comunicaciones](https://docs.fastly.com/guides/securing-communications/) (documentación de Fastly)

## Versiones afectadas

* **Adobe Commerce en la infraestructura en la nube:**
   * versión: 2.1.4 y posterior
   * planes: Adobe Commerce en la infraestructura en la nube Arquitectura del plan inicial y Adobe Commerce en la infraestructura en la nube Arquitectura del plan Pro (incluido el programa heredado Pro)
* **Rápidamente:** 1.2.4

## No se necesitan cambios en routes.yaml

Para habilitar el redireccionamiento de HTTP a HTTPS en **todas** las páginas de tu tienda, no tienes que agregar las páginas al archivo de configuración de `routes.yaml`; basta con habilitar Forzar TLS globalmente para todo tu almacén (usando el administrador de Commerce).

## Documentación de Fastly relacionada

* [Forzar guía TLS para Adobe Commerce 2](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/FORCE-TLS.md)
* [Forzando una redirección TLS](https://docs.fastly.com/guides/securing-communications/forcing-a-tls-redirect)
* [Proteger comunicaciones](https://docs.fastly.com/guides/securing-communications/)
