---
title: Actualice al esquema DHL v10 para seguir ofreciendo el envío DHL
description: Este artículo proporciona una solución para permitir a los comerciantes seguir ofreciendo el envío DHL después de que el esquema DHL 6.2 quede obsoleto en diciembre de 2022, actualizando al esquema 10.0 o aplicando el parche AC-3023.
exl-id: eed83713-2d6a-4360-bfa1-bebd4d604f2f
feature: Orders, Shipping/Delivery, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# Actualice a la versión 10.0 del esquema DHL para seguir ofreciendo el envío DHL

Este artículo proporciona una solución para permitir que los comerciantes sigan ofreciendo el envío DHL después de que la versión de esquema 6.2 de DHL quede obsoleta a finales de diciembre de 2022.

## Productos y versiones afectados

* Adobe Commerce 2.4.5 y versiones anteriores, todos métodos de implementación.

## Problema

En agosto de 2022, lanzamos la [actualización del esquema DHL versión 6.2. junto con un parche ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/adobe-commerce-dhl-upgrade-patch.html) para que los comerciantes sigan ofreciendo el envío DHL. DHL volverá a introducir un esquema más reciente (versión 10.0) en octubre de 2022, y la versión anterior (esquema 6.2) quedará obsoleta a finales de diciembre de 2022. La integración de Adobe Commerce 2.4.5 y versiones anteriores de DHL solo admite la versión 6.2.

## Solución

Adobe Commerce 2.4.5-p1 y 2.4.4-p2, publicadas en octubre de 2022, contienen la nueva versión de esquema DHL 10.0. Así que los comerciantes que actualizan a 2.4.5-p1 y 2.4.4-p2 no tienen que hacer nada para seguir ofreciendo los envíos de DHL. Recomendamos a todos los comerciantes que actualicen a 2.4.5-p1 y 2.4.4-p2 antes de que DHL schema 6.2 quede obsoleto a finales de diciembre de 2022.

Los comerciantes que no deseen actualizar a 2.4.5-p1 y 2.4.4-p2 deberán aplicar un parche si desean seguir ofreciendo el envío DHL después de diciembre de 2022.

## Parche

El identificador de parche es AC-3023 y está disponible en la versión 1.1.21 de [!DNL Quality Patches Tool].

Consulte los siguientes vínculos sobre cómo usar [!DNL Quality Patches Tool] e instalar parches según los métodos de implementación:

* Magento Open Source y local de Adobe Commerce: [Herramientas de parches de calidad > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en Adobe Experience League.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

**La revisión es aplicable a las siguientes versiones de Adobe Commerce (todos los métodos de implementación):**

* 2.3.7, 2.4.0, 2.4.1, 2.4.2, 2.4.3, 2.4.3-p2, 2.4.3-p3, 2.4.4

## Vínculos útiles

* [[!DNL Quality Patches Tool] > Notas de la versión](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) en Adobe Experience League.

* [[!DNL Quality Patches Tool]: buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en Adobe Experience League.

## Lectura relacionada

* [Aplique un parche para seguir ofreciendo DHL como transportista](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/adobe-commerce-dhl-upgrade-patch.html) en nuestra base de conocimiento de soporte.

* [Transportistas de envío > DHL](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/delivery/shipping-carriers/dhl.html) en nuestra guía de usuario.
* [Referencia de configuración > Ventas > Métodos de envío](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/delivery-methods.html) en nuestra guía de usuario.
