---
title: Configuración de NPM para poder utilizar PWA Studio
description: '''[Progressive Web Apps (PWA) Studio](https://magento.github.io/pwa-studio/) es un nuevo proyecto disponible para Adobe Commerce en la infraestructura en la nube 2.3.x o posterior. Para poder utilizar e instalar PWA Studio, debe establecer la versión del administrador de paquetes NPM en 5.x o posterior para obtener soporte para Node.js 8.x. Esto se hace en la sección "hooks:build" del archivo de configuración ".magento.app.yaml".'
exl-id: 3854fc94-e8ad-45d8-bf3e-73462364220d
source-git-commit: 37ac9cca1f876a48092467aa38f2f2f013c83dd9
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Configuración de NPM para poder utilizar PWA Studio

[Progressive Web Apps (PWA) Studio](https://magento.github.io/pwa-studio/) es un nuevo proyecto disponible para Adobe Commerce en la infraestructura en la nube 2.3.x o posterior. Para poder utilizar e instalar PWA Studio, debe establecer la versión del administrador de paquetes NPM en 5.x o posterior para obtener soporte para Node.js 8.x. Esto se hace en la sección `hooks:build` del archivo de configuración `.magento.app.yaml`.

## Entorno y tecnologías

* Adobe Commerce en la infraestructura en la nube 2.3.X
* PWA para Adobe Commerce

## Establecer versión de NPM: pasos

Para establecer la versión de NPM necesaria, especifíquela en el archivo de configuración `.magento.app.yaml`. Siga estos pasos:

1. En su entorno de desarrollo local, busque el archivo de configuración `.magento.app.yaml`.
1. Abra el archivo para editarlo con el editor de texto sin formato o IDE.
1. Establezca la versión requerida en la sección `hooks:build`. En el siguiente ejemplo, la configuración está configurada para instalar NPM v9.5.0, el más alto disponible en este momento (4 de febrero de 2019):

   ```yaml
   hooks:
       build: |
           unset NPM_CONFIG_PREFIX
           curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash
           export NVM_DIR="$HOME/.nvm"
           [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
           nvm install 9.5.0
   ```

   >[!NOTE]
   >
   >Si desea ejecutar Node.JS en la aplicación y no solo en la compilación, agregue los siguientes comandos para cambiar el vínculo de compilación:
   > 
   > ```
   > echo 'unset NPM_CONFIG_PREFIX' >> .environment
   > echo 'export NO_UPDATE_NOTIFIER=1' >> .environment
   > echo 'export NVM_DIR="$MAGENTO_CLOUD_DIR/.nvm"' >> .environment
   > echo '[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"' >> .environment
   > ```

1. Guarde los cambios en el archivo.
1. Git inserta el archivo editado en tu [entorno de integración](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md).

Los cambios entrarán en vigor después de que Git inserte el archivo YAML actualizado en el entorno.

## Documentación relacionada

* [Configuración de la aplicación: enlaces](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/hooks-property.html?lang=es) en nuestra Guía de infraestructura de Adobe Commerce en la nube.
