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

El parche ACSD-51471 corrige el problema en el que un usuario administrador no puede guardar una actualización programada para un producto agrupado que utiliza un producto simple con una actualización programada. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 está instalado. El ID del parche es ACSD-51471. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios administradores no pueden guardar una actualización programada para un producto agrupado que utiliza un producto simple que tiene una actualización programada.

<u>Pasos a seguir</u>:

1. Cree un producto sencillo.
1. Añada una actualización programada para el producto simple con solo la variable *Fecha de inicio* y no *Fecha de finalización*.
1. Una vez aplicada la actualización, cambie el SKU del producto.
1. Cree un producto agrupado y añada el producto simple creado en el paso 1 como producto secundario.
1. Cree una actualización programada para el producto agrupado para habilitar el producto agrupado. Proporcione ambos *Fecha de inicio* y *Fecha de finalización* para la actualización programada.
1. Guarde la actualización programada.

<u>Resultados esperados</u>:

La actualización programada se ha guardado correctamente.

<u>Resultados reales</u>:

Se produce el siguiente error al guardar la actualización programada: *El producto solicitado no existe. Compruebe el producto e inténtelo de nuevo.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
