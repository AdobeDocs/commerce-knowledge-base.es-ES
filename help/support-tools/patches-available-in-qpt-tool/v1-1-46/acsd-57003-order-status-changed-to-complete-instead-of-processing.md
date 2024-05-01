---
title: "ACSD-57003: El estado del pedido cambia a *Completo* en lugar de cambiar a *Procesando*"
description: Aplique el parche ACSD-57003 para corregir el problema de Adobe Commerce en el que el estado del pedido cambia a *Completado* en lugar de cambiar a *Procesando*.
feature: Orders, Invoices, Shipping/Delivery
role: Admin, Developer
exl-id: c3c59185-c447-46fa-b404-6c4a4a300315
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-57003: El estado del pedido cambia a *Completar* en lugar de cambiar a *Procesando*

El parche ACSD-57003 corrige el problema en el que el estado del pedido cambia a *Completar* en lugar de cambiar a *Procesando*. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.46 está instalado. El ID del parche es ACSD-57003. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El estado del pedido cambia a *Completar* en lugar de cambiar a *Procesando* cuando un pedido se reembolsa parcialmente y se envía parcialmente.

<u>Pasos a seguir</u>:

1. Cree un pedido con dos productos configurables.
1. Facturar todos los artículos.
1. Enviar solo el primer artículo.
1. Devolver o crear una nota de abono solo para el artículo enviado (*primer elemento*).
1. Compruebe el estado del pedido.

<u>Resultados esperados</u>:

El estado del pedido debe ser el siguiente _Procesando_ estado.

<u>Resultados reales</u>:

El estado de los pedidos cambia a *Completar* después de crear una nota de abono para el artículo enviado parcialmente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
