---
title: "parche del Magento MDVA-23426: correos electrónicos enviados como archivos adjuntos desde Outlook"
description: El parche del Magento MDVA-23426 corrige el problema en el que los correos electrónicos se envían como archivos adjuntos por Magento desde MS Outlook. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13. Tenga en cuenta que el problema se solucionó en el Magento 2.3.5.
exl-id: 0b4c3e33-76c5-48b0-b1a8-a967cea11b98
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Parche del Magento MDVA-23426: correos electrónicos enviados como archivos adjuntos desde Outlook

El parche del Magento MDVA-23426 corrige el problema en el que los correos electrónicos se envían como archivos adjuntos por Magento desde MS Outlook. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13. Tenga en cuenta que el problema se solucionó en el Magento 2.3.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Magento:** Magento Commerce Cloud 2.3.3.

**Compatible con versiones de Magento:** Magento Commerce y Magento Commerce Cloud 2.3.3 - 2.3.4-p2.

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los correos electrónicos se reciben con un cuerpo en blanco y el contenido se incluye como archivo adjunto.

<u>Requisitos previos:</u> Outlook/Exchange se está usando como combinación de cliente y servidor.

<u>Pasos a seguir:</u> 1. Envíe un pedido, se enviará la notificación de pedido o la notificación de envío.2. Se recibe el correo electrónico.

<u>Resultado real:</u> El correo electrónico se muestra con un cuerpo en blanco y el contenido incluido como datos adjuntos con la etiqueta ATT\* al correo electrónico. <u>Resultado esperado:</u>

El correo electrónico se recibe sin archivos adjuntos y el cuerpo del correo electrónico contiene el contenido.

## Aplicar el parche

Para obtener instrucciones sobre cómo aplicar un parche QPT, utilice los siguientes enlaces según el producto de su Magento:

* Magento Commerce: DevDocs [Aplicar parches usando la herramienta Parches de calidad](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) .
* Magento Commerce Cloud: DevDocs [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) .

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) .
* [Compruebe el parche para el problema del Magento con la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) .

Para obtener información sobre otros parches disponibles en la herramienta QPT, consulte la sección [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
