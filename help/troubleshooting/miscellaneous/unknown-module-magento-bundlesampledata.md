---
title: 'Módulo desconocido: Magento_BundleSampleData'
description: Este artículo proporciona una corrección para el error de módulo desconocido durante la instalación de Adobe Commerce.
exl-id: c927bc8f-d70b-4305-87c1-223001212555
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Módulo desconocido: Magento_BundleSampleData

Este artículo proporciona una corrección para el error de módulo desconocido durante la instalación de Adobe Commerce.

## Problema {#details}

Durante la instalación, aparece un mensaje similar al siguiente:

```text
[ERROR] exception 'LogicException' with message 'Unknown module in the requested list: 'Magento_BundleSampleData''
```

## Solución {#solution}

Pruebe cada una de las siguientes opciones a la vez y vuelva a intentar la instalación.

1. Ejecute el Asistente para configuración web. Los módulos se enumeran en  **Configuraciones avanzadas de módulos**. Para deshabilitar la variable **Magento\_BundleSampleData** módulo, borre el **Magento\_BundleSampleData** como se muestra en la figura siguiente.

   ![shoot_bundlesampledata.png](assets/tshoot_bundlesampledata.png)

1. Borre todo el historial y los datos del explorador web.
1. Si tiene Chrome, borre todos los datos del explorador relacionados con el sitio.  Ir a **Configuración** > **Opciones avanzadas** > **Privacidad** > **Configuración de contenido** > **Todas las cookies y los datos del sitio**. En la columna Sitio, haga clic en la dirección del servidor de Adobe Commerce y seleccione **Eliminar todo**.
