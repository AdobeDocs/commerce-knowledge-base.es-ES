---
title: '"ACSD-49502: El vínculo descargable no se actualizó correctamente después de [!DNL staging] update'''
description: Aplique el parche ACSD-49502 para corregir el problema de Adobe Commerce en el que el vínculo descargable no se actualiza correctamente después de un [!DNL staging] la actualización se aplica al producto descargable.
exl-id: 9e7f0c06-4b7d-42c4-8ec7-cdeefd7e8a08
feature: Staging
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-49502: el vínculo descargable no se actualiza correctamente después de [!DNL staging] actualizar

El parche ACSD-49502 corrige el problema en el que el vínculo descargable no se actualiza correctamente después de un [!DNL staging] la actualización se aplica al producto descargable. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 está instalado. El ID del parche es ACSD-49502. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El vínculo descargable no se actualiza correctamente después de un [!DNL staging] la actualización se aplica al producto descargable.

<u>Pasos a seguir</u>:

1. Cree un producto descargable con vínculos.
1. Cree una cuenta de cliente e inicie sesión.
1. Añadir el producto descargable al carro de compras desde la tienda.
1. En el **[!UICONTROL Admin]**, programe una nueva actualización para el producto descargable y deje que se complete la actualización programada.
1. Complete el pedido en la tienda.

<u>Resultados esperados</u>:

Los vínculos descargables se conservan al utilizar actualizaciones programadas mientras los productos añadidos anteriormente están en el carro de compras.

<u>Resultados reales</u>:

Faltan vínculos descargables en los vínculos del cliente *[!UICONTROL My Account]* ([!UICONTROL My Downloadable Products]) y páginas de vista de pedidos en  **[!UICONTROL Admin]**.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
