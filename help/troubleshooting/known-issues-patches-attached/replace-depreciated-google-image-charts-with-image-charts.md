---
title: Reemplazar gráficos de imágenes de Google depreciados por gráficos de imágenes
description: Actualmente, la mayoría de las ediciones y versiones de Adobe Commerce utilizan [Google Image Charts](https://developers.google.com/chart/image/) para representar gráficos estáticos en los paneles de administración. A partir del 14 de marzo de 2019, Google dejará de admitir gráficos de imágenes de Google. Para resolver este problema, proporcionamos un parche para reemplazar los gráficos de imágenes de Google con un servicio gratuito de [gráficos de imágenes](https://www.image-charts.com/).
exl-id: f86f0bb9-8a03-471d-8696-1eba4b8acbd1
feature: Cache, Compliance
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# Reemplazar gráficos de imágenes de Google depreciados por gráficos de imágenes

La mayoría de las ediciones y versiones de Adobe Commerce utilizan actualmente [Gráficos de imagen de Google](https://developers.google.com/chart/image/) para procesar gráficos estáticos en los paneles de administración. A partir del 14 de marzo de 2019, Google dejará de admitir gráficos de imágenes de Google. Para resolver este problema, proporcionamos un parche para reemplazar los gráficos de imágenes de Google por [Image-Charts](https://www.image-charts.com/) servicio gratuito.

## Versiones afectadas

* Adobe Commerce 1.X, todas las ediciones
* Adobe Commerce 2.X, todas las ediciones

>[!NOTE]
>
>Adobe Commerce local 1.14.4.1, Magento Open Source 1.9.4.1, Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.2 incluirán esta actualización del gráfico. La actualización a estas versiones sigue siendo compatible con los gráficos de imágenes sin parches adicionales.

## Problema

Google dejó de admitir gráficos de imágenes de Google el 14 de marzo de 2019. Los usuarios de Adobe Commerce 1.X y Adobe Commerce 2.2.X de todas las versiones no podrán ver los gráficos estáticos a menos que descarguen y apliquen el parche y sustituyan los gráficos de imágenes de Google por la solución Image-Charts. Los gráficos mostrados tendrán el mismo diseño y funcionalidad que los gráficos de imágenes de Google a través del servicio de cuenta gratuita Image-Charts con un [RGPD](https://www.image-charts.com/data-processing-addendum.html) directiva de privacidad de cumplimiento. Para ver opciones adicionales, consulte [Image-Charts](https://www.image-charts.com/).

## Solución

Para poder ver gráficos estáticos en el administrador de Commerce, descargue y aplique el parche proporcionado por Adobe Commerce. No es necesaria ninguna configuración adicional.

### Adobe Commerce local

1. Guarde el [adjunto MAGETWO-98833\_composer\_patch-2019-04-15-04-38-57.patch](assets/MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch.zip) aplique el parche y cárguelo en el directorio raíz de Adobe Commerce.
1. Ejecute el siguiente comando SSH, habiendo sustituido el nombre del parche por uno real:

   ```git
   patch -p1 < MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch
   ```

   Si el comando anterior no funciona, intente utilizar `-p2` en lugar de `-p1`.)

1. Para que se reflejen los cambios, actualice la caché en el Administrador en **Sistema** > **Administración de caché**.

### Adobe Commerce en la infraestructura en la nube

Para los comerciantes de Cloud, el parche se incluirá en la actualización de herramientas ECE más cercana.

### Magento 2 Open Source

1. Ir a [https://magento.com/tech-resources/download\#download2291](https://magento.com/tech-resources/download#download2291).
1. En el **Seleccione el formato** , seleccione la versión de composición y haga clic en **Descargar**.
1. Cargue el parche en el directorio raíz de Adobe Commerce.
1. Ejecute el siguiente comando SSH, habiendo sustituido el nombre del parche por uno real:

   ```git
   patch -p1 < MAGETWO-98833_composer_patch-2019-04-15-04-37-48.patch
   ```

   (Si el comando anterior no funciona, intente utilizar `-p2` en lugar de `-p1`.)

1. Para que se reflejen los cambios, actualice la caché en el Administrador en **Sistema** > **Administración de caché**.

### Adobe Commerce 1 local

Siga estos pasos para descargar y aplicar el parche:

1. Guarde el [adjunto MPERF-10509-EE-2019-03-13-06-32-19.diff](assets/MPERF-10509-EE-2019-03-13-06-32-19.diff.zip) aplique el parche y cárguelo en el directorio raíz de Adobe Commerce.
1. Ejecute el siguiente comando SSH:

   ```git
   patch -p1 < MPERF-10509-EE-2019-03-13-06-32-19.diff
   ```

   (Si el comando anterior no funciona, intente utilizar `-p2` en lugar de `-p1`.)

1. Para que se reflejen los cambios, actualice la caché en el Administrador en **Sistema** > **Administración de caché**.

### Magento 1 Código abierto

Siga estos pasos para descargar y aplicar el parche:

1. Clic [**este vínculo**](https://magento.com/tech-resources/download#download2283) para localizar el parche de gráficos del tablero de administración.
1. Seleccionar

   ```git
   MPERF-10509.diff
   ```

   desde el **Seleccione el formato** y haga clic en Descargar.

1. Cargue el archivo en el directorio raíz de Adobe Commerce.
1. Ejecute el siguiente comando SSH:

   ```git
   patch -p1 < MPERF-10509.diff
   ```

   (Si el comando anterior no funciona, intente utilizar `-p2` en lugar de `-p1`.)

1. Para que se reflejen los cambios, actualice la caché en el Administrador en **Sistema** > **Administración de caché**.

## Archivos adjuntos

[Descargar MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch](assets/MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch)

[Descargar MPERF-10509-EE-2019-03-13-06-32-19.diffh](assets/MPERF-10509-EE-2019-03-13-06-32-19.diff)
