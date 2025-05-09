---
title: "ACSD-51471: el usuario administrador no puede guardar la actualización programada para el producto agrupado"
description: Aplique el parche ACSD-51471 para corregir el problema de Adobe Commerce en el que un usuario administrador no puede guardar una actualización programada para un producto agrupado que utiliza un producto simple con una actualización programada.
exl-id: 7d80aef0-8505-4491-bde3-5b1a30b840f6
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# ACSD-51471: el usuario administrador no puede guardar la actualización programada para el producto agrupado

El parche ACSD-51471 corrige el problema en el que un usuario administrador no puede guardar una actualización programada para un producto agrupado que utiliza un producto simple con una actualización programada. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33. El ID del parche es ACSD-51471. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios administradores no pueden guardar una actualización programada para un producto agrupado que utiliza un producto simple que tiene una actualización programada.

<u>Pasos a seguir</u>:

1. Cree un producto sencillo.
1. Agregue una actualización programada para el producto simple con solo la *Fecha de inicio* y sin *Fecha de finalización*.
1. Una vez aplicada la actualización, cambie el SKU del producto.
1. Cree un producto agrupado y añada el producto simple creado en el paso 1 como producto secundario.
1. Cree una actualización programada para el producto agrupado para habilitar el producto agrupado. Proporcione *Fecha de inicio* y *Fecha de finalización* para la actualización programada.
1. Guarde la actualización programada.

<u>Resultados esperados</u>:

La actualización programada se ha guardado correctamente.

<u>Resultados reales</u>:

El siguiente error se produce al guardar la actualización programada: *El producto solicitado no existe. Compruebe el producto y vuelva a intentarlo.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
