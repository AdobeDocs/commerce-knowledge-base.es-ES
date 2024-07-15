---
title: Solicitar correo electrónico enviado desde la dirección de correo electrónico del servidor
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce en la infraestructura en la nube 2.2.4 relacionado con los correos electrónicos de pedido que se envían desde la dirección de correo electrónico del servidor.
exl-id: f32e0c09-e19e-4269-bbba-0533d74a7f49
feature: Communications
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Solicitar correo electrónico enviado desde la dirección de correo electrónico del servidor

Este artículo proporciona un parche para el problema conocido de Adobe Commerce en la infraestructura en la nube 2.2.4 relacionado con los correos electrónicos de pedido que se envían desde la dirección de correo electrónico del servidor.

## Problema

Los correos electrónicos de confirmación de pedido se envían desde la dirección de correo electrónico del servidor Apache. Otros correos electrónicos (contraseña olvidada, etc.) se envían desde las direcciones de correo electrónico configuradas.

<u>Pasos a seguir</u>:

1. Realice un pedido con la casilla **Enviar confirmación de pedido** marcada.
1. Compruebe el correo electrónico.

<u>Resultado esperado</u>:

El correo electrónico se ha enviado desde la dirección de envío configurada para Adobe Commerce.

<u>Resultado real</u>:

El correo electrónico se envió desde la dirección de correo electrónico configurada en el servidor Apache que se está utilizando.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[Descargar MDVA-10993\_EE\_2.2.4\_v1.composer.patch](assets/MDVA-10993_EE_2.2.4_v1.composer.patch.zip)

### Versiones de Adobe Commerce compatibles:

El parche se ha creado para:

* Adobe Commerce en la infraestructura en la nube 2.2.4

El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce en infraestructura en la nube 2.2.5
* Adobe Commerce en infraestructura en la nube 2.2.6
* Adobe Commerce en infraestructura en la nube 2.2.7
* Adobe Commerce en infraestructura en la nube 2.2.8
* Adobe Commerce local 2.2.4
* Adobe Commerce local 2.2.5
* Adobe Commerce local 2.2.6
* Adobe Commerce local 2.2.7
* Adobe Commerce local 2.2.8
* Adobe Commerce local 2.3.0

## Cómo aplicar el parche

Para obtener instrucciones, consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de soporte.

## Archivos adjuntos
