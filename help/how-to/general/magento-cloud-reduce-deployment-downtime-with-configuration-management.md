---
title: Reduzca el tiempo de inactividad de la implementación en Adobe Commerce en la infraestructura en la nube
description: Para reducir drásticamente el tiempo de inactividad del mantenimiento y proporcionar una configuración eficiente de su tienda en todos los entornos, Adobe Commerce en la infraestructura en la nube proporciona la función **Administración de configuración**. Para Adobe Commerce en implementaciones de infraestructura en la nube 2.2.x y posteriores, esta función admite conceptos y opciones de implementación de canalización con pasos reducidos.
exl-id: fde3571c-d95c-4a9b-a024-3b29f9c491ab
feature: Build, Cloud, Configuration, Deploy
source-git-commit: 23d957ceac17f9989d14b215582304199d398545
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# Reduzca el tiempo de inactividad de la implementación en Adobe Commerce en la infraestructura en la nube

Para reducir drásticamente el tiempo de inactividad durante el mantenimiento y proporcionar una configuración eficiente de su tienda en todos los entornos, Adobe Commerce en la infraestructura en la nube proporciona el **Administración de configuración** función. Para Adobe Commerce en implementaciones de infraestructura en la nube 2.2.x y posteriores, esta función admite conceptos y opciones de implementación de canalización con pasos reducidos.

## Información general

Los problemas laboriosos y laboriosos de implementar su tienda web incluyen:

* **Aplicar la misma configuración en todos los entornos.** Normalmente, las configuraciones se introducen manualmente o mediante complicadas actualizaciones de la base de datos. Con la administración de la configuración, exporte las configuraciones de la base de datos a un solo archivo para insertarlo posteriormente con el código del entorno de desarrollo local en Integración, Ensayo y Producción.

* **Tiempo de inactividad del sitio al implementar contenido estático.** Normalmente, el contenido estático se implementa durante el [fase de implementación](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#deploy-phase-deploy-phase). Esto puede tardar hasta 30 minutos o más, lo que no es aceptable para los negocios. Administración de configuración mueve la implementación de contenido estático a [fase de compilación](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#build-phase-build-phase), que no requiere tiempo de inactividad.

## Versiones tecnológicas

* Adobe Commerce en la infraestructura en la nube **2.1.4** y posterior para la administración de la configuración
* Adobe Commerce en la infraestructura en la nube **2,2** y posterior para la administración de configuración/implementación de canalización

## Qué es la administración de configuración

Para resumir, el proceso de administración de configuración (también conocido como implementación de canalización) extrae todos los ajustes de configuración de su Adobe Commerce en la implementación de infraestructura en la nube (base de datos) en un solo archivo PHP. A continuación, agregue el archivo a la confirmación de Git y presiónelo en todos los entornos.

Esto ofrece las siguientes ventajas:

* **Configuración coherente en todos los entornos:** cualquier configuración que se exporte al archivo de configuración se bloqueará (los campos correspondientes del administrador de Commerce pasarán a ser de solo lectura), lo que garantiza configuraciones coherentes a medida que inserta el archivo en todos los entornos.
* **Tiempo de inactividad reducido:** la implementación del archivo estático cambia de la [fase de implementación](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#deploy-phase-deploy-phase) (que requiere que el sitio esté en modo de mantenimiento) a la [fase de compilación](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#build-phase-build-phase) (cuando el sitio no está en modo de mantenimiento y no se desactivará si se producen errores o problemas).
* **Datos confidenciales protegidos:** con Adobe Commerce en la infraestructura en la nube 2.2 y versiones posteriores, el proceso también exporta cualquier dato confidencial (por ejemplo, credenciales de puerta de enlace de pago) a `env.php` archivo. Este archivo solo debe guardarse en el entorno en el que se crea y no insertarse con las ramas de Git.

Se recomienda encarecidamente aplicar el método de administración de la configuración en la implementación.

## Administración de la configuración en nuestra documentación para desarrolladores

* [Administración de configuración para **2.1.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) y el [ejemplo](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) en el *Guía de Adobe Commerce sobre la infraestructura en la nube*
* [Administración de configuración para **2.2.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) y el [ejemplo](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) en el *Guía de Adobe Commerce sobre la infraestructura en la nube*
* [Actualización de 2.0.X o 2.1.X](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html#upgrade-from-older-versions) de la sección *Actualización de Adobe Commerce en la infraestructura en la nube* tema
* [Implementación de canalización](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/overview.html) en el *Guía de configuración de Adobe Commerce en la nube* : Para Adobe Commerce en la infraestructura en la nube, no es necesario seguir las instrucciones de esta guía. El contenido es estrictamente de referencia. Ya proporcionamos el servidor de compilación, los entornos de integración y mucho más con Adobe Commerce en la infraestructura en la nube.
