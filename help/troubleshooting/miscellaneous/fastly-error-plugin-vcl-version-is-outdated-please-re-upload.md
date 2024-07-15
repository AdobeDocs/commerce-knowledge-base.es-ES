---
title: '"Fastly Error: La versión de VCL del complemento está obsoleta! Vuelva a cargar.'
description: Este artículo proporciona una solución para cuando vea el mensaje "*La versión del complemento VCL está obsoleta. Vuelva a cargarlo.*" en Configuración de Fastly, en el Administrador de Commerce, debido a que no ha instalado el módulo de Fastly más reciente.
exl-id: d7870e9e-ba6b-49c2-a80c-26fb464cbae3
feature: Best Practices, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Error de Fastly: La versión de VCL del complemento está obsoleta. Vuelva a cargar

Este artículo proporciona una solución para cuando vea el mensaje &quot;*La versión del complemento VCL está obsoleta. Vuelva a cargarlo.*&quot; en la configuración de Fastly, en el administrador de Commerce, debido a que no se ha instalado el módulo de Fastly más reciente.

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube 2.2.x., 2.3.x<br>
Fastly: Este error puede afectar a todas las versiones del módulo Fastly, excepto a la más reciente. Para obtener información sobre la versión más reciente, consulte [Notas de la versión de Fastly](https://github.com/fastly/fastly-magento2/releases) en GitHub.

## Problema

1. Inicie sesión en el panel de administración de Commerce.
1. Vaya a **Tiendas** > **Configuración** > **Avanzado** > **Sistema** > **Caché de página completa**   **Caché de Fastly.**
1. En la sección **Activación automática de carga y servicio**, habrá una &quot;*versión del complemento VCL obsoleta. Vuelva a cargarlo.Notificación*&quot;.
1. Intenta cargar los fragmentos de VCL haciendo clic en el botón &quot;Cargar VCL a Fastly&quot;, pero aún ve la advertencia &quot;*La versión de VCL del complemento está obsoleta. Vuelva a subir.*&quot;

## Causa

La extensión de Fastly se actualizó (junto con una configuración de VCL agrupada y plantillas), pero la configuración de VCL actualizada no se ha cargado al servicio de Fastly. Al actualizar el módulo de Adobe Commerce `Fastly_Cdn`, debe volver a cargar una configuración de VCL actualizada en Fastly.

## Solución

1. Compruebe que tiene instaladas las herramientas ECE-Tools más recientes y en la [versión actual](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html) de nuestra documentación para desarrolladores. ECE-Tools tiene una versión del paquete Fastly en sus dependencias.

   Esta puede no ser la última versión del complemento Fastly, pero es probable que sea una versión posterior a la que tiene instalada actualmente, y es una práctica recomendada tener instalada la última ECE-Tools.

1. Si no se encuentra en la versión actual de ECE-Tools, siga estos pasos para [actualizar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) en nuestra documentación para desarrolladores.
1. Después de haber actualizado ECE-Tools, verifique si ahora tiene instalada una versión actual del [plugin de Fastly](https://github.com/fastly/fastly-magento2/tree/master/etc/vcl_snippets).
1. Si el complemento de Fastly no es la versión actual, siga estos pasos para [actualizar el complemento a la versión más actual](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#upgrade-the-fastly-module) en nuestra documentación para desarrolladores.

## Lectura relacionada

* Para obtener información sobre cómo configurar Fastly, consulte [Configurar servicios de Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html) en nuestra documentación para desarrolladores.
* Para obtener información general sobre Fastly, consulte [fastly.com](https://www.fastly.com/).
