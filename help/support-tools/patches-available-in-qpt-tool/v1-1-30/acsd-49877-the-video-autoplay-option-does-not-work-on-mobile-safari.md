---
title: '"ACSD-49877: La reproducción automática de vídeo no funciona en dispositivos móviles [!DNL Safari]'''
description: Aplique el parche ACSD-49877 para solucionar el problema de Adobe Commerce en el que la opción de reproducción automática de vídeo no funciona en dispositivos móviles [!DNL Safari] cuando el vídeo está vinculado directamente a un archivo de vídeo remoto.
exl-id: 454f7cec-29b9-485b-93be-2a4f2eb77da7
feature: CMS
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-49877: La reproducción automática de vídeo no funciona en dispositivos móviles [!DNL Safari]

El ACSD-49877 corrige el problema en el que la opción de reproducción automática en móviles [!DNL Safari] no funciona cuando el vídeo está vinculado directamente a un archivo de vídeo remoto. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 está instalado. El ID del parche es ACSD-49877. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el [!magento/parches de calidad] paquete a la última versión y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: buscar parches]. Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La reproducción automática de vídeo no funciona en dispositivos móviles [!DNL Safari] cuando el vídeo está vinculado directamente a un archivo de vídeo remoto y no a un servicio de streaming.

<u>Requisitos previos</u>:
[!DNL Page Builder] módulos están instalados.

<u>Pasos a seguir</u>:

1. Cree una nueva página de CMS y edite la **[!UICONTROL Content Value]** con [!DNL Page Builder].
1. Añadir un *Ficha* al contenido y añada un elemento *Elemento de vídeo* dentro de *Ficha*.
1. Ahora haga clic en el botón de engranaje para editar el *Elemento de vídeo*.
1. Añada un vínculo a un archivo de vídeo mp4 a [!UICONTROL Video URL] field.
1. Marcar el **[!UICONTROL Autoplay]** campo como *Sí*.
1. Clic **[!UICONTROL Save]**.
1. Abra la página creada recientemente en [!DNL Safari] uso de una iPhone.

<u>Resultados esperados</u>

La opción de reproducción automática funciona en [!DNL Safari] uso de una iPhone.

<u>Resultados reales</u>

La opción de reproducción automática no funciona en [!DNL Safari] uso de una iPhone.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
