---
title: "No se puede eliminar el archivo. ¡Advertencia! desvincular: no existe el error de archivo o directorio en el [!DNL Admin]"
description: Este artículo proporciona una solución al problema en el que ve un error * El archivo no se puede eliminar. Advertencia!desvincular No existe ese error de archivo o directorio* del [!DNL Admin] cuando realice una [!DNL Javascript/CSS] al ras.
feature: Admin Workspace, Observability
role: Developer
exl-id: db265e3c-a809-4404-839a-273001e81d22
source-git-commit: fd5fd6e1bc04db56497a2e0c2a96bc1b06d4f7a1
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# *No se puede eliminar el archivo. Advertencia: no existe el archivo o error de directorio* desde el [!DNL Admin]

Este artículo proporciona una solución al problema en el que ve un error *No se puede eliminar el archivo. Advertencia: no existe el archivo o error de directorio* desde el [!DNL Commerce Admin] cuando realice una [!DNL JavaScript/CSS] al ras.

## Productos y versiones afectados

* Adobe Commerce 2.4.0 - 2.4.6, todos los métodos de implementación

## Problema

Se produce un error al realizar una [!DNL JS/CSS] vaciar:

*El archivo &quot;/app/pub/static/_cache/merged/.nfsa42d0e64799fd1000000001b&quot; no se puede eliminar. Warning!unlink(/app/pub/static/_cache/merged/.nfsa42d0e64799fd1000000001b): No existe ese archivo o directorio*

O bien: Verá el error anterior en la [!DNL Admin], y/o un error similar en [!DNL New Relic] o en los registros de implementación.

O: No puede acceder a los informes avanzados y el trabajo cron analytics_collect_data está fallando con este error:

*El archivo &quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0&quot; no se puede eliminar. Advertencia!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0): No existe ese archivo o directorio*

<u>Pasos a seguir:</u>

Método 1:

1. Inicie sesión en [!DNL Admin].
1. Ir a **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Clic **[!UICONTROL Flush][!DNL JavaScript/CSS][!UICONTROL Cache]**.

Método 2:

1. Inicie sesión en [!DNL Admin].
1. Ir a **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**.
1. Realice cambios en la [!UICONTROL Base URL] o [!UICONTROL Base URL (Secure)].
1. Haga clic en **[!UICONTROL Save Config]**.

## Solución

Si utiliza Adobe Commerce en una infraestructura en la nube y tiene [!DNL magento/magento-cloud-patches] 1.0.22 instalado que incluye el parche, no es necesario instalar por separado ACSD-50165.

Adobe Commerce en infraestructura en la nube: Actualizar parches de la nube para Commerce a 1.0.22 (**o más reciente**) que contiene esta corrección: [Parches de nube para Commerce](/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html).

Adobe Commerce local: Aplique ACSD-50165 mediante [Parches de calidad > Herramientas > Uso](/docs/commerce-operations/tools/quality-patches-tool/usage.html). El parche ACSD-50165 viene con [!DNL QPT] [Versión 1.1.30.](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html#v1-1-30)

## Lectura relacionada

* [[!DNL Quality Patches Tool] > Notas de la versión](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) en la guía Herramientas de Commerce.
* [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía Herramientas de Commerce.
