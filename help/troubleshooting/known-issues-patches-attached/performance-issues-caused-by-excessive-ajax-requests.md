---
title: Problemas de rendimiento causados por un exceso de solicitudes de Ajax
description: Este artículo proporciona un parche para el problema de rendimiento conocido de Adobe Commerce causado por un exceso de solicitudes de Ajax. El problema se solucionó en Adobe Commerce 2.3.4.
exl-id: d9a69406-3970-4556-aa6a-1309b24366d8
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# Problemas de rendimiento causados por un exceso de solicitudes de Ajax

Este artículo proporciona un parche para el problema de rendimiento conocido de Adobe Commerce causado por un exceso de solicitudes de Ajax. El problema se solucionó en Adobe Commerce 2.3.4.

## Problema

Es posible que Adobe Commerce esté enviando [solicitudes de Ajax](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md) redundantes desde la tienda al servidor para obtener la información del banner y la información del cliente. Estas solicitudes de Ajax tienen un impacto en el rendimiento, especialmente en condiciones de alta carga (gran volumen y alto tráfico). Por lo tanto, si no se usa la funcionalidad Banner, se recomienda [deshabilitar por completo la salida del módulo Banner de Adobe Commerce](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md) y aplicar el parche para mejorar la recuperación de información del cliente.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[Descargue el MDVA-24597\_EE\_2.2.9\_COMPOSER\_v1.patch](assets/MDVA-24597_EE_2.2.9_COMPOSER_v1.patch.zip)

### Versiones de Adobe Commerce compatibles

El parche es válido para los siguientes productos y versiones:

* Adobe Commerce en la infraestructura en la nube 2.2.9
* Adobe Commerce local 2.2.9

Si tiene una versión diferente de Adobe Commerce, considere la posibilidad de actualizar a la última versión 2.3.x. Si esta no es una opción actualmente, comuníquese con el [soporte técnico de Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) y solicite un parche para su versión.

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obtener instrucciones.

## Archivos adjuntos
