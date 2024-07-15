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

El botón **Crear una cuenta** de la página **Crear nueva cuenta** permanece deshabilitado si un comprador ha especificado datos no válidos. Esto evita que los compradores vuelvan a intentar crear una cuenta después de cometer un error.

<u>Pasos a seguir</u>:

1. Vaya a **Crear nueva cuenta de cliente**.
1. Rellene los campos del formulario. En el campo **Contraseña**, introduzca valores que no cumplan los requisitos de contraseña. Por ejemplo:
   * Las contraseñas de los campos **Password** y **Confirm Password** no coinciden.
   * Las contraseñas de los campos **Password** y **Confirm Password** no son lo suficientemente largas.
1. Haga clic en el botón **Crear una cuenta**.

<u>Resultados esperados</u>:

* El botón **Crear una cuenta** debe permanecer activo/habilitado.
* El usuario debe poder crear una nueva cuenta.

<u>Resultados reales</u>:

* El botón **Crear una cuenta** permanece deshabilitado, incluso después de rellenar todos los campos obligatorios con datos válidos o correctos.
* El cliente no puede crear una cuenta nueva.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre de archivo o en el vínculo siguiente: [Descargar MC-38509-composer.patch](assets/MC-38509-composer.patch.zip)

## Versiones de Adobe Commerce compatibles:

El parche se ha creado para:

* Adobe Commerce en la infraestructura en la nube 2.3.6 y 2.4.1.
* Adobe Commerce local 2.3.6 y 2.4.1.

El parche no es compatible con ninguna otra versión ni edición de Adobe Commerce.

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obtener instrucciones.

## Lectura relacionada

* [GitHub Adobe Commerce > Al enviar un formulario de creación de cuenta no válido, se desactiva el botón de envío](https://github.com/magento/magento2/issues/30513)
* [Guía del usuario de Adobe Commerce > Introducción > Creación de una cuenta](https://docs.magento.com/user-guide/magento/magento-account-create.html)
