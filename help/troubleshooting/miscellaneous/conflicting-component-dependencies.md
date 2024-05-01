---
title: Dependencias de componentes en conflicto
description: Este artículo proporciona una solución para las dependencias de componentes en conflicto. Al intentar configurar o actualizar Adobe Commerce mediante el Asistente para configuración web, verá el mensaje de error *"Hemos encontrado dependencias de componentes en conflicto"* Compositor.
exl-id: 782049c4-b6e1-4ead-a00f-80d2aa8475c9
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# Dependencias de componentes en conflicto

Este artículo proporciona una solución para las dependencias de componentes en conflicto. Al intentar configurar o actualizar Adobe Commerce mediante el Asistente para instalación web, verá el *&quot;Encontramos dependencias de componentes en conflicto&quot;* Mensaje de error del compositor.

## Productos y versiones afectados

* Adobe Commerce local 2.2.x, 2.3.x
* Adobe Commerce en cloud Infrastructure 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x


## Problema {#issue}

Un mensaje de error de dependencias de componentes en conflicto similar al siguiente (los nombres y versiones reales de los paquetes variarán):

```bash
We found conflicting component dependencies.
You are trying to update package(s) magento/module-sample-data to 1.0.0-beta
We have detected conflicts with the following packages:
- magento/sample-data version 0.74.0-beta15. Please try to update it to one of the following package versions: 0.74.0-beta16, 0.74.0-beta14, 0.74.0-beta13, 0.74.0-beta12, 0.74.0-beta11, 0.74.0-beta10, 0.74.0-beta9, 0.74.0-beta8, 0.74.0-beta7
```

## Causa

Este mensaje aparece si Composer no puede determinar qué componentes instalar o actualizar.

## Solución

Dos escenarios principales pueden provocar dependencias de componentes en conflicto. Haga clic en su escenario para obtener los pasos de solución de problemas.

* [Actualización de Adobe Commerce](#upgrading-magento)
* [Incompatibilidad con módulos de terceros:](#incompatibility-third-party-modules)
   * [Adobe Commerce (todos los tipos de implementación)](#magento-commerce-magento-commerce-cloud)
   * [Magento Open Source](#opensource)

## Actualización de Adobe Commerce {#upgrading-magento}

Si actualiza Adobe Commerce en una infraestructura en la nube, intente lo siguiente para resolver las dependencias de componentes en conflicto:

* Compruebe las claves que se están utilizando para actualizar. ¿Las claves se generan a partir de la cuenta de correo electrónico correcta?
* Compruebe los permisos y asegúrese de que coinciden con los requisitos de actualización del Magento. Revisar [Información general sobre la actualización de Magento > Actualizar y actualizar lista de comprobación > Permisos del sistema de archivos](https://devdocs.magento.com/guides/v2.3/comp-mgr/prereq/prereq_compman-checklist.html#perms) en nuestra documentación para desarrolladores.

## Incompatibilidad con módulos de terceros: {#incompatibility-third-party-modules}

Las dependencias de componentes en conflicto también pueden deberse a módulos de terceros que dependen de componentes de Commerce anteriores a los instalados. Pruebe lo siguiente:

1. En el anterior [ejemplo](#issue), el paquete instalado magento/sample-data versión 0.74.0-beta15 no se puede actualizar a 1.0.0-beta. Sin embargo, 0.74.0-beta15 se puede actualizar a 0.74.0-beta16 (u otros). Editar `composer.json` para realizar cualquiera de estos cambios. Normalmente, las versiones que solicita el proyecto se definen en la variable `require` o `require-dev` propiedad del objeto en ese archivo JSON. Según las opciones de las versiones de paquetes proporcionadas, pueden especificar una versión específica o una restricción. Para obtener instrucciones generales sobre cómo usar Composer, si está en nuestra infraestructura de nube, puede consultar [Cloud for Adobe Commerce > Tecnologías y requisitos > Compositor](https://devdocs.magento.com/cloud/reference/cloud-composer.html#files) en nuestra documentación para desarrolladores. Si utiliza Adobe Commerce local, consulte [Adobe Commerce > Guía de instalación > Instalar Adobe Commerce con el Compositor](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html) .
1. Ahora pruebe la comprobación de disponibilidad. Revisar [Información general sobre la actualización de Adobe Commerce > Ejecutar el administrador de módulos > Comprobación de preparación para el paso 1](https://devdocs.magento.com/guides/v2.3/comp-mgr/module-man/compman-readiness.html) en nuestra documentación para desarrolladores.
1. Si la comprobación de disponibilidad falla con otro mensaje de error en la comprobación de dependencias del componente, haga clic en los siguientes vínculos en función de si está utilizando [Adobe Commerce](#magento-commerce-magento-commerce-cloud) o [Magento Open Source](#opensource) para obtener más información sobre la resolución de problemas.

## Adobe Commerce {#magento-commerce-magento-commerce-cloud}

1. Póngase en contacto con el desarrollador de la extensión para que pueda ayudarle. Puede encontrar su información de contacto en la página en la que compró la extensión en el Commerce Marketplace. Busque la variable **Contactar con vendedor** botón mostrado en el panel derecho. Todos los desarrolladores de Commerce deben proporcionar una guía de usuario e instalación cuando publiquen una extensión en Marketplace. Puede encontrar ambas en el lado derecho de su página de aterrizaje.
1. Si no recibe una respuesta del Vendedor en un plazo razonable, le rogamos [informar al Commerce Marketplace](https://marketplacesupport.magento.com/hc/en-us) para que podamos recordarles sus compromisos de asistencia al cliente.

## Magento Open Source {#opensource}

Solicite asistencia en [nuestro foro principal](https://community.magento.com/) o [póngase en contacto con un socio de Adobe Commerce](https://magento.com/find-a-partner) que ayuda en los problemas de código abierto.
