---
title: Error "El área ya está establecida" al guardar la configuración del tema en Administración
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce en la infraestructura en la nube 2.2.4 relacionado con la obtención del mensaje de error *"El área ya está establecida"* al intentar establecer una temática para la vista de tienda predeterminada en el administrador de Commerce.
exl-id: c4e34a73-b774-4447-ba8e-aaf208ad54c5
feature: Admin Workspace, Configuration, Themes
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Error &quot;El área ya está establecida&quot; al guardar la configuración del tema en el administrador

Este artículo proporciona un parche para el problema conocido de Adobe Commerce en la infraestructura en la nube 2.2.4 relacionado con la obtención de la *&quot;El área ya está configurada&quot;* mensaje de error al intentar establecer una temática para la vista de tienda predeterminada en el administrador de Commerce.

## Problema

Obtienes el &quot; *Se ha producido un error al guardar esta configuración: el área ya está definida* Mensaje de error &quot; al intentar establecer una temática para la vista de tienda predeterminada.

<u>Pasos a seguir</u>:

1. Inicie sesión en el administrador de Commerce.
1. Vaya a **Contenido** > **Diseño** > **Configuración**.
1. Establezca el ámbito de configuración en *Vista de tienda predeterminada*.
1. Cambie la temática en la **Tema aplicado** menú desplegable. Por ejemplo, desde *Luma* hasta *En blanco.*
1. Clic **Guardar configuración**.

<u>Resultado esperado</u>: el tema seleccionado se aplica a la vista de tienda predeterminada.

<u>Resultado real</u> : El tema no se aplica, el *&quot;Se ha producido un error al guardar esta configuración: el área ya está configurada&quot;* se muestra un mensaje de error.

## Parche

El parche se adjunta a este artículo. Para descargarlo, haga clic en el siguiente vínculo o desplácese hacia abajo hasta el final del artículo y haga clic en el archivo adjunto:

[Descargar MDVA-11106\_EE\_2.2.4\_v1.composer.patch](assets/MDVA-11106_EE_2.2.4_v1.composer.patch.zip)

## Versiones de Adobe Commerce compatibles:

El parche se ha creado para:

* Adobe Commerce en la infraestructura en la nube 2.2.4

El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce en la infraestructura en la nube 2.0.X
* Adobe Commerce en la infraestructura en la nube 2.1.X
* Adobe Commerce en infraestructura en la nube 2.2.0 - 2.2.5
* Adobe Commerce local 2.0.X
* Adobe Commerce local 2.1.X
* Adobe Commerce local 2.2.0 - 2.2.5

## Cómo aplicar el parche

Para obtener instrucciones, consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de soporte.

## Archivos adjuntos
