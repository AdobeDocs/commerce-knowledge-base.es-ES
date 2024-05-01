---
title: El pago por ciberfuente desde el administrador y el front en diferentes dominios no se procesa
description: Este artículo proporciona un parche para la limitación conocida de Adobe Commerce 2.3.0 relacionada con la falta de la capacidad de procesar pagos de fuentes cibernéticas desde la tienda y el administrador de Commerce, si están en dominios diferentes.
exl-id: 948d5907-70bd-4890-bc8a-23e04b116018
feature: Admin Workspace, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# El pago por ciberfuente desde el administrador y el front en diferentes dominios no se procesa

Este artículo proporciona un parche para la limitación conocida de Adobe Commerce 2.3.0 relacionada con la falta de la capacidad de procesar pagos de fuentes cibernéticas desde la tienda y el administrador de Commerce, si están en dominios diferentes.

>[!NOTE]
>
>La integración principal de pagos de Adobe Commerce Cybersource está obsoleta desde la versión 2.3.3 y se eliminará completamente en la versión 2.4.0. Utilice el [extensión oficial](https://marketplace.magento.com/cybersource-global-payment-management.html) del mercado en su lugar.

## Problema

La implementación anterior de la integración de Cybersource permitía procesar pagos de un solo dominio. Como resultado, si la tienda de Adobe Commerce está en un dominio diferente al de la administración de Commerce, se produce el siguiente error al intentar realizar un pedido con Cybersource en la administración: &quot; *Carga denegada por X-Frame-Options: https://%your\_domain%/cybersource/SilentOrder/TokenResponse/ no permite tramas de origen cruzado.* ..&quot;

<u>Pasos a seguir</u>:

1. Configure el administrador en un subdominio diferente.
1. Configure Cybersource para la tienda en **Tiendas** > Configuración > **Configuración** > **Ventas** > **Métodos de pago** > **CyberSource**.
1. Ir a **Ventas** > **Pedidos**.
1. Cree un nuevo pedido.
1. Crear nuevo cliente.
1. Introduzca los detalles del cliente.
1. Especifique los detalles del pedido (productos, método de envío).
1. Seleccione Cybersource como método de pago.
1. Envíe el pedido.

<u>Resultado esperado</u>: el pedido se realiza sin problemas.

<u>Resultado real</u>: La página Pedido muestra un icono de carga, pero el pedido nunca se realiza. El error se muestra en la consola.

## Solución

El parche adjunto proporciona la mejora para la integración con Cybersource. Después de aplicar el parche, debe crear otro perfil con Cybersource para procesar pagos en el administrador y añadir las credenciales necesarias en la configuración de Cybersource en el administrador de Commerce en **Tiendas** > Configuración > **Configuración** > **Ventas** > **Métodos de pago** > **CyberSource**.

>[!NOTE]
>
>La mejora se incluye en las infraestructuras locales y en la nube de Adobe Commerce 2.2.9 y 2.3.1.

## Parche

Hay varios parches adjuntos a este artículo, diferentes parches para diferentes versiones. Para descargar un parche, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

* [Descargar MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch](assets/MDVA-5914_EE_2.1.9_COMPOSER_v3.patch.zip)
* [Descargar MDVA-8609\_EE\_2.2.2\_COMPOSER\_v2.patch](assets/MDVA-8609_EE_2.2.2_COMPOSER_v2.patch.zip)
* [Descargar MDVA-12964\_EE\_2.2.5\_COMPOSER\_v1.patch](assets/MDVA-12964_EE_2.2.5_COMPOSER_v1.patch.zip)
* [Descargar MDVA-16643\_EE\_2.3.0\_COMPOSER\_v1.patch](assets/MDVA-16643_EE_2.3.0_COMPOSER_v1.patch.zip)

## Versiones de Adobe Commerce compatibles

Los parches se han creado para una versión concreta indicada en el nombre del archivo de parche. Por ejemplo, MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch se creó para Adobe Commerce 2.1.9 y es el mejor parche que se puede usar para esta versión.

Los parches también son compatibles con las siguientes versiones:

* Adobe Commerce local 2.1.3-2.1.17; Adobe Commerce en infraestructura en la nube 2.1.5-2.12 (MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch)
* Adobe Commerce local 2.2.0-2.2.3; Adobe Commerce en infraestructura en la nube 2.2.0-2.2.3 (MDVA-8609\_EE\_2.2.2\_COMPOSER\_v2.patch)
* Adobe Commerce local 2.2.4-2.2.7; Adobe Commerce en infraestructura en la nube 2.2.4-2.2.7 (MDVA-12964\_EE\_2.2.5\_COMPOSER\_v1.patch)
* Adobe Commerce local 2.2.8, 2.3.0; Adobe Commerce en infraestructura en la nube 2.3.0 (MDVA-16643\_EE\_2.3.0\_COMPOSER\_v1.patch)

## Cómo aplicar un parche

Para obtener instrucciones, consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de soporte.

## Archivos adjuntos
