---
title: "ACSD-49737: El cupón se marca incorrectamente como utilizado después de un pago con tarjeta fallido"
description: Aplique el parche ACSD-49737 para corregir el problema de Adobe Commerce en el que el cupón se marca incorrectamente como utilizado después de un pago con tarjeta fallido.
exl-id: 77b5ec9c-3c4c-4da3-ba7e-8be3ccea04d0
feature: Orders, Payments
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-49737: el cupón se marcó incorrectamente como *usado* después de un pago con tarjeta erróneo

El parche ACSD-49737 corrige el problema en el que el cupón se marca incorrectamente como *usado* después de un pago con tarjeta erróneo. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30. El ID del parche es ACSD-49737. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1-p1 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El cupón se marcó incorrectamente como *usado* después de un pago con tarjeta erróneo.

<u>Requisitos previos</u>:

1. Configure el método **[!UICONTROL Braintree sandbox payment]**.
1. Asegúrese de que el consumidor [*sales.rule.update.coupon.usage*](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/message-queues/consumers.html?lang=es) esté configurado y en ejecución.

<u>Pasos a seguir</u>:

1. Crear un **[!UICONTROL Cart Price Rule]** con códigos de cupones generados automáticamente.
1. Inicie sesión como cliente.
1. Añadir productos al carro de compras.
1. Aplique un código de cupón generado automáticamente.
1. Intente realizar un pedido con un pago fallido.
1. Compruebe el uso del cupón en **[!UICONTROL Cart Price Rule]**, en la ficha **[!UICONTROL Manage Coupon Codes]**.

<u>Resultados esperados</u>:

El cupón no debería marcarse como *usado* si se produce un error en el pago.

<u>Resultados reales</u>:

* El código de cupón indica - Usado: *Yes*, tiempos usados: *1*
* El código de cupón es válido para un solo uso de tiempo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Pasos adicionales necesarios tras la instalación del parche

(Esta sección es opcional; es posible que se requieran algunos pasos después de aplicar el parche para solucionar el problema). 

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
