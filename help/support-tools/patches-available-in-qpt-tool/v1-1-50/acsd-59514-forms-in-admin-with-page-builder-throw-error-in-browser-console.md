---
title: "ACSD-59514: Forms en el administrador con  [!DNL Page Builder] error de activación en la consola del explorador"
description: Aplique el parche ACSD-59514 para corregir el problema de Adobe Commerce en el que los formularios en el administrador con  [!DNL Page Builder] emiten el error "[!DNL Page Builder] se representaban durante 5 segundos sin liberar bloqueos". en la consola del explorador después de enviar el formulario, y los cambios no se pueden guardar.
feature: Page Builder
role: Admin, Developer
source-git-commit: 19ecaa6b287d63bfae00c51911b53e1ed7ab5ed8
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---


# ACSD-59514: Forms en el administrador con error de lanzamiento [!DNL Page Builder] en la consola del explorador

El parche ACSD-59514 corrige el problema en el que los formularios del administrador con [!DNL Page Builder] generaban el error *[!DNL Page Builder]durante 5 segundos sin liberar bloqueos.* en la consola del explorador después de enviar el formulario, y no se pueden guardar los cambios. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50. El ID del parche es ACSD-59514. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p8

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Forms en administración con [!DNL Page Builder] produjo el error *[!DNL Page Builder]que se estaba representando durante 5 segundos sin liberar bloqueos.* en la consola del explorador después de enviar el formulario, y no se pueden guardar los cambios.

<u>Requisitos previos</u>:

Los módulos de Adobe Commerce [!DNL Page Builder] están instalados y habilitados.

<u>Pasos a seguir</u>:

1. Abra el panel de administración y haga clic en el botón [!UICONTROL Content].
1. Seleccione el bloque y edítelo.
1. Cambie el contenido y haga clic en [!UICONTROL Save].
1. Abra la consola y vea el mensaje de error.

<u>Resultados esperados</u>:

El bloque se ha guardado correctamente.

<u>Resultados reales</u>:

El cargador no deja de girar y el bloque no se guarda. El siguiente error se muestra en la consola del explorador:
*[!DNL Page Builder]se representó durante 5 segundos sin liberar bloqueos.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].