---
title: Fecha incorrecta para el precio especial
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.2.2 relacionado con el precio especial del producto "desde" fecha que es incorrecta si su valor lo cambia el administrador cuya configuración regional de interfaz es diferente.
exl-id: fc109550-951e-4900-97e3-4ff3e7e5a395
feature: Orders, Personalization, User Account
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Fecha incorrecta para el precio especial

Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.2.2 relacionado con el precio especial del producto &quot;desde&quot; fecha que es incorrecta si su valor lo cambia el administrador cuya configuración regional de interfaz es diferente.

## Problema

Cuando establece o cambia el precio especial de un producto, la fecha y la hora actuales se guardan en la base de datos como un valor para el atributo `special_from_date` (no visible al editar un producto). Si edita el precio especial y su cuenta de usuario de administrador está configurada en una configuración regional de interfaz diferente, podría establecerse un valor incorrecto en `special_from_date` debido a los problemas al analizar el formato de fecha para diferentes configuraciones regionales.

<u>Pasos a seguir</u>:

Requisitos previos: la configuración regional del usuario administrador es inglés (Estados Unidos).

1. Inicie sesión en el administrador de Commerce.
1. Vaya a la configuración de la cuenta de usuario de administrador.
1. Configure la Configuración regional de la interfaz a Ucraniano.
1. Haga clic en **Guardar cuenta**.
1. Vaya a **Catálogo** > **Producto**.
1. Seleccione cualquier producto.
1. En la página de productos, haz clic en **Precios avanzados**.
1. Añade un precio especial.
1. Guarde el producto.
1. Repita los pasos 7-9.
1. Vaya a **Sistema** > **Registros de acciones**.
1. Compruebe el registro para ver si hay actualizaciones del producto.

<u>Resultados esperados</u>:

La fecha de inicio del precio especial debe ser la fecha actual.

<u>Resultados reales</u>:

La fecha de inicio del precio especial es una fecha de unos años en el futuro, lo que impide que el precio especial esté activo.

## Solución

Si se aplica el parche, el problema no se volverá a producir. Para corregir los datos de los productos en los que la fecha se estableció incorrectamente, vuelva a establecer el precio especial después de aplicar el parche.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[Descargar MDVA-11605\_EE\_2.2\_COMPOSER\_v1.patch](assets/MDVA-11605_EE_2.2.2_COMPOSER_v1.patch.zip)

### Versiones de Adobe Commerce compatibles:

El parche se ha creado para:

* Adobe Commerce (todos los métodos de implementación) 2.2.2

El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce local 2.1.0-2.1.18, 2.2.0-2.2.5
* Adobe Commerce en infraestructura en la nube 2.1.11-2.1.18, 2.2.0-2.2.5

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obtener instrucciones.

## Archivos adjuntos
