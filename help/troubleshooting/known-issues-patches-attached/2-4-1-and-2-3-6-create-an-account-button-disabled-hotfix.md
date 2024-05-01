---
title: Revisión deshabilitada del botón Crear cuenta de Adobe Commerce 2.4.1 y 2.3.6
description: Este artículo proporciona una revisión del problema que se produce cuando se lucha por crear una cuenta nueva después de introducir un valor incorrecto en cualquier campo del formulario. Por ejemplo, cuando introduce una dirección de correo electrónico con un formato incorrecto, deja vacíos los campos de nombre o apellido o no introduce un valor que cumpla los requisitos de contraseña. Se incluirá una corrección permanente en las versiones del primer trimestre (2.4.2, 2.4.1-p1 y 2.3.6-p1).
exl-id: e6e65ede-8156-4e2b-b369-b18395bb3dbf
feature: Customer Service
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# Revisión deshabilitada del botón Crear cuenta de Adobe Commerce 2.4.1 y 2.3.6

Este artículo proporciona una revisión del problema que se produce cuando se lucha por crear una cuenta nueva después de introducir un valor incorrecto en cualquier campo del formulario. Por ejemplo, cuando introduce una dirección de correo electrónico con un formato incorrecto, deja vacíos los campos de nombre o apellido o no introduce un valor que cumpla los requisitos de contraseña. Se incluirá una corrección permanente en las versiones del primer trimestre (2.4.2, 2.4.1-p1 y 2.3.6-p1).

## Problema

El **Crear una cuenta** botón en el **Crear nueva cuenta** La página permanece deshabilitada si un comprador ha introducido datos no válidos. Esto evita que los compradores vuelvan a intentar crear una cuenta después de cometer un error.

<u>Pasos a seguir</u>:

1. Ir a **Crear nueva cuenta de cliente**.
1. Rellene los campos del formulario. En el **Contraseña** , valores de entrada que no cumplen los requisitos de contraseña. Por ejemplo:
   * Las contraseñas de **Contraseña** y el **Confirmar contraseña** los campos no coinciden.
   * Las contraseñas de **Contraseña** y el **Confirmar contraseña** los campos no son lo suficientemente largos.
1. Haga clic en **Crear una cuenta** botón.

<u>Resultados esperados</u>:

* **Crear una cuenta** El botón debe permanecer activo/activado.
* El usuario debe poder crear una nueva cuenta.

<u>Resultados reales</u>:

* **Crear una cuenta** El botón permanece desactivado, incluso después de rellenar todos los campos obligatorios con datos válidos o correctos.
* El cliente no puede crear una cuenta nueva.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo: [Descargar MC-38509-composer.patch](assets/MC-38509-composer.patch.zip)

## Versiones de Adobe Commerce compatibles:

El parche se ha creado para:

* Adobe Commerce en la infraestructura en la nube 2.3.6 y 2.4.1.
* Adobe Commerce local 2.3.6 y 2.4.1.

El parche no es compatible con ninguna otra versión ni edición de Adobe Commerce.

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obtener instrucciones.

## Lectura relacionada

* [GitHub Adobe Commerce > Enviar formulario de creación de cuenta no válido deja desactivado el botón de envío](https://github.com/magento/magento2/issues/30513)
* [Guía del usuario de Adobe Commerce > Introducción > Creación de una cuenta](https://docs.magento.com/user-guide/magento/magento-account-create.html)
