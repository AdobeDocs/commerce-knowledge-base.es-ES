---
title: Dependencias de componentes en conflicto
description: Este artículo proporciona una solución para las dependencias de componentes en conflicto. Al intentar configurar o actualizar Adobe Commerce mediante el Asistente para configuración web, verá el mensaje de error *"Hemos encontrado dependencias de componentes en conflicto"* Compositor.
exl-id: 782049c4-b6e1-4ead-a00f-80d2aa8475c9
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# Dependencias de componentes en conflicto

Este artículo proporciona una solución para las dependencias de componentes en conflicto. Al intentar configurar o actualizar Adobe Commerce mediante el Asistente para configuración web, verá el mensaje de error *&quot;Encontramos dependencias de componentes en conflicto&quot;* del Compositor.

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
* Compruebe los permisos y asegúrese de que coinciden con los requisitos de actualización del Magento. Revise [Información general sobre la actualización del Magento > Actualizar y actualizar lista de comprobación > Permisos del sistema de archivos](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/prerequisites#verify-file-system-permissions) en nuestra documentación para desarrolladores.

## Incompatibilidad con módulos de terceros: {#incompatibility-third-party-modules}

Las dependencias de componentes en conflicto también pueden deberse a módulos de terceros que dependen de componentes de Commerce anteriores a los instalados. Pruebe lo siguiente:

1. En el [ejemplo](#issue) anterior, el paquete instalado magento/sample-data versión 0.74.0-beta15 no se puede actualizar a 1.0.0-beta. Sin embargo, 0.74.0-beta15 se puede actualizar a 0.74.0-beta16 (u otros). Edite `composer.json` para realizar cualquiera de estos cambios. Normalmente, las versiones que solicita el proyecto se definirán en la propiedad `require` o `require-dev` del objeto de ese archivo JSON. Según las opciones de las versiones de paquetes proporcionadas, pueden especificar una versión específica o una restricción. Para obtener instrucciones generales sobre cómo usar Composer, si está en nuestra infraestructura de nube, puede consultar [Cloud for Adobe Commerce > Technologies and Requirements > Composer](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview#files) en nuestra documentación para desarrolladores. Si se encuentra en Adobe Commerce local, consulte [Adobe Commerce > Guía de instalación > Instalar Adobe Commerce mediante Composer](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/composer) .
1. Ahora pruebe la comprobación de disponibilidad. Revise [Información general sobre la actualización de Adobe Commerce > Ejecutar el administrador de módulos > Comprobación de preparación para el paso 1](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/overview) en nuestra documentación para desarrolladores.
1. Si la comprobación de disponibilidad falla con otro mensaje de error en la comprobación de dependencias del componente, haga clic en los siguientes vínculos en función de si está usando [Adobe Commerce](#magento-commerce-magento-commerce-cloud) o [Magento Open Source](#opensource) para obtener más pasos con la solución de problemas.

## Adobe Commerce {#magento-commerce-magento-commerce-cloud}

1. Póngase en contacto con el desarrollador de la extensión para que pueda ayudarle. Puede encontrar su información de contacto en la página en la que compró la extensión en el Commerce Marketplace. Busca el botón **Contactar con el vendedor** que aparece en el panel derecho. Todos los desarrolladores de Commerce deben proporcionar una guía de usuario e instalación cuando publiquen una extensión en Marketplace. Puede encontrar ambas en el lado derecho de su página de aterrizaje.
1. Si no recibe una respuesta del vendedor en un período de tiempo razonable, [comuníquese con la atención al cliente](mailto:commercemarketplacesupport@adobe.com) para que podamos recordarle sus compromisos de atención al cliente.

## Magento Open Source {#opensource}

Solicite asistencia en [nuestro foro principal](https://community.magento.com/) o [póngase en contacto con un socio de Adobe Commerce](https://magento.com/find-a-partner) que ayude con los problemas de Open Source.
