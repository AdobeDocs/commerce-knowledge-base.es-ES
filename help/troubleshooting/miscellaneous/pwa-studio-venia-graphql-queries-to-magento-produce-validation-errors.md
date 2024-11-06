---
title: "PWA Studio: las consultas de Venia GraphQL a Adobe Commerce producen errores de validación"
description: Este artículo proporciona recomendaciones sobre cómo resolver el problema en el que las consultas de GraphQL de la tienda Venia a la instancia de Adobe Commerce producen errores de validación.
exl-id: ba268945-2a10-4af5-8089-cde21f0687bd
feature: GraphQL
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# PWA Studio: las consultas de Venia GraphQL a Adobe Commerce producen errores de validación

Este artículo proporciona recomendaciones sobre cómo resolver el problema en el que las consultas de GraphQL de la tienda Venia a la instancia de Adobe Commerce producen errores de validación.

## Productos y versiones afectados

* Adobe Commerce local 2.2.x, 2.3.x
* Adobe Commerce en cloud Infrastructure 2.2.x, 2.3.x
* proyecto de PWA Studio para Adobe Commerce

## Problema

Las consultas de Venia GraphQL a Adobe Commerce local o a Adobe Commerce en la infraestructura en la nube producen errores de validación.

## Causa

Una de las razones que causa el problema es que Venia y sus consultas de GraphQL no están sincronizadas con el esquema de la instancia de Adobe Commerce conectada.

## Solución

Para probar si las consultas están actualizadas, ejecute el siguiente comando en la raíz del proyecto:

```bash
yarn run validate-queries
```

Se mostrará un informe de compatibilidad. Si tiene incompatibilidades, debe actualizar la instancia de PWA Studio o Adobe Commerce. Compruebe la [matriz de compatibilidad de Adobe Commerce](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/version-compatibility/) para ver exactamente qué versiones necesita.

Consulte la siguiente documentación para obtener instrucciones sobre cómo actualizar:

* Para actualizaciones de PWA Studio, busque la sección &quot;Actualización desde una versión anterior&quot; de [Notas de la versión de PWA](https://github.com/magento/pwa-studio/releases/) para la versión a la que necesita actualizar.
* [Actualice Adobe Commerce en la versión de infraestructura en la nube](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) en nuestra documentación para desarrolladores.
* [Actualice Adobe Commerce local (instalado usando &quot;composer create-project&quot; o archivo)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) en nuestra documentación para desarrolladores.
* [Actualice Adobe Commerce local (instalado mediante la clonación del repositorio de Adobe Commerce)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/developer/git-installs) en nuestra documentación para desarrolladores.

## Lectura relacionada

* [PWA Studio: Webpack se bloquea antes de comenzar la compilación](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md) en nuestra base de conocimiento de soporte
* [PWA Studio: errores de validación al ejecutar el modo de desarrollador](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md) en nuestra base de conocimiento de soporte
* [PWA Studio: el explorador muestra el error &quot;No se puede proxy a&quot;](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md) en nuestra base de conocimiento de soporte
* [Configuración de NPM para poder usar PWA Studio](/help/how-to/general/configure-npm-to-be-able-to-use-pwa-studio.md) en nuestra base de conocimiento de soporte
* [PWA para la documentación de Adobe Commerce](https://magento.github.io/pwa-studio/)
