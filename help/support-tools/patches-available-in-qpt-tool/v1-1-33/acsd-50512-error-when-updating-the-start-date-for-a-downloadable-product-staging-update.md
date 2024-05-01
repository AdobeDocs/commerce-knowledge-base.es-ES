---
title: "ACSD-50512: Error al actualizar la fecha de inicio de una actualización de ensayo de producto descargable"
description: Aplique el parche ACSD-51892 para corregir el problema de rendimiento de Adobe Commerce donde el error *El vínculo descargable no está relacionado con el producto.Compruebe el vínculo e inténtelo de nuevo*, se produce al actualizar la fecha de inicio de una actualización de ensayo de producto descargable.
feature: Products, Staging
role: Admin
exl-id: 873357ef-49c3-48f8-a98e-41c48cb9ba8b
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# ACSD-50512: Error al actualizar la fecha de inicio de la actualización descargable del ensayo del producto

El parche ACSD-50512 corrige el problema donde el error *El vínculo descargable no está relacionado con el producto. Compruebe el vínculo e inténtelo de nuevo*, se produce al actualizar la fecha de inicio de una actualización de ensayo de producto descargable. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.33 está instalado. El ID del parche es ACSD-51502. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El error *El vínculo descargable no está relacionado con el producto. Compruebe el vínculo e inténtelo de nuevo*, se produce al actualizar la fecha de inicio de una actualización de ensayo de producto descargable.

<u>Pasos a seguir</u>:

1. Cree un producto descargable con *vínculos descargables* y *vínculos de muestra*.
1. Cree una actualización programada para el mismo producto y guarde el producto.
1. Edite la actualización programada preconfigurada (del paso 2) y cambie la fecha de inicio.
1. Guarde la actualización programada.

<u>Resultados esperados</u>:

Los cambios realizados en la actualización programada se han guardado correctamente.

<u>Resultados reales</u>:

Recibe el siguiente error: *El vínculo descargable no está relacionado con el producto. Compruebe el vínculo e inténtelo de nuevo*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
