---
title: "No se puede eliminar el archivo. ¡Advertencia! desvincular: no existe el error de archivo o directorio del  [!DNL Admin]"
description: 'Este artículo proporciona una solución al problema en el que ve un error * El archivo no se puede eliminar. Advertencia: no se puede desvincular ese archivo o error de directorio* de  [!DNL Admin]  cuando se realiza el vaciado de  [!DNL Javascript/CSS] .'
feature: Admin Workspace, Observability
role: Developer
exl-id: db265e3c-a809-4404-839a-273001e81d22
source-git-commit: fd5fd6e1bc04db56497a2e0c2a96bc1b06d4f7a1
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# *No se puede eliminar el archivo. Advertencia: no existe el error de archivo o directorio* del [!DNL Admin]

Este artículo proporciona una solución al problema donde se muestra un error *El archivo no se puede eliminar. Advertencia: no existe el error de archivo o directorio* del [!DNL Commerce Admin] cuando se realiza el vaciado de [!DNL JavaScript/CSS].

## Productos y versiones afectados

* Adobe Commerce 2.4.0 - 2.4.6, todos los métodos de implementación

## Problema

Se produce un error al vaciar [!DNL JS/CSS]:

*No se puede eliminar el archivo &quot;/app/pub/static/_cache/merged/.nfsa42d0e64799fd1000000001b&quot;. Advertencia!unlink(/app/pub/static/_cache/merged/.nfsa42d0e64799fd1000000001b): no existe ese archivo o directorio*

O: Verá el error anterior en [!DNL Admin], o un error similar en [!DNL New Relic] o en los registros de implementación.

O: No puede acceder a los informes avanzados y el trabajo cron analytics_collect_data está fallando con este error:

*No se puede eliminar el archivo &quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0&quot;. Advertencia!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0): No existe ese archivo o directorio*

<u>Pasos a seguir:</u>

Método 1:

1. Inicie sesión en [!DNL Admin].
1. Ir a **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Haga clic en **[!UICONTROL Flush][!DNL JavaScript/CSS][!UICONTROL Cache]**.

Método 2:

1. Inicie sesión en [!DNL Admin].
1. Vaya a **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**.
1. Realice cambios en [!UICONTROL Base URL] o [!UICONTROL Base URL (Secure)].
1. Haga clic en **[!UICONTROL Save Config]**.

## Solución

Si está en una infraestructura de Adobe Commerce en la nube y tiene instalado [!DNL magento/magento-cloud-patches] 1.0.22, que incluye el parche, no necesita instalar por separado ACSD-50165.

Adobe Commerce en la infraestructura de la nube: Actualice los parches de la nube para Commerce a la versión 1.0.22 (**o posterior**), que contiene esta corrección: [Parches de la nube para Commerce](/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html).

Adobe Commerce local: aplique ACSD-50165 con [Herramientas de parches de calidad > Uso](/docs/commerce-operations/tools/quality-patches-tool/usage.html). La revisión ACSD-50165 viene con [!DNL QPT] [v1.1.30.](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html#v1-1-30)

## Lectura relacionada

* [[!DNL Quality Patches Tool] > Notas de la versión](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) en la guía de herramientas de Commerce.
* [[!DNL Quality Patches Tool]: busque parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía de herramientas de Commerce.
