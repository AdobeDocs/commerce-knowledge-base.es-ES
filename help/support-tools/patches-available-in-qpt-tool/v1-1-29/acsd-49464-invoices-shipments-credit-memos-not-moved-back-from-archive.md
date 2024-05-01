---
title: "ACSD-49464: facturas, envíos y notas de abono que no se han movido del archivo"
description: Aplique el parche ACSD-49464 para solucionar el problema de Adobe Commerce en el que las facturas, los envíos y los abonos no se mueven de vuelta del archivo cuando orderId es diferente.
exl-id: 845f9878-5f7e-4e58-8f8a-b02af17b3f11
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-49464: facturas, envíos y notas de abono que no se han movido del archivo

El parche ACSD-49464 corrige el problema en el que las facturas, los envíos y los abonos no se mueven de nuevo del archivo cuando orderId es diferente. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 está instalado. El ID del parche es ACSD-49464. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las facturas, los envíos y los abonos no se mueven de vuelta del archivo cuando orderId es diferente.

<u>Pasos a seguir</u>:

1. Activar el archivado de pedidos, facturas, envíos y notas de abono.
1. Cree y complete un pedido, incluidos el envío, la factura y la nota de abono.
1. Asegúrese de que los ID de envío, de factura y de nota de abono no sean los mismos que el número de pedido.
1. Mueva el orden para archivar.
1. Restaure el pedido archivado en Order Management.
1. Compruebe los detalles de la factura, el envío y la nota de abono en los respectivos [!UICONTROL Invoice], [!UICONTROL Shipping], y [!UICONTROL Credit Memo] páginas de cuadrícula.

<u>Resultados esperados</u>:

Los registros relacionados originales se restauran cuando el orden se mueve de la lista de archivos a la administración de pedidos.

<u>Resultados reales</u>:

* No hay registros para el envío, la factura y las notas de abono si todos los ID son diferentes.
* Si el pedido y los registros relacionados tienen el mismo ID, se devuelven los registros.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
