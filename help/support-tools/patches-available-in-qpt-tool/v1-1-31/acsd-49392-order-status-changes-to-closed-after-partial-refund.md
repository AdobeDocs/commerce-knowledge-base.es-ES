---
title: "ACSD-49392: El estado del pedido cambia a cerrado después del reembolso parcial"
description: Aplique el parche ACSD-49392 para solucionar el problema de Adobe Commerce en el que el estado del pedido cambia a cerrado después de un reembolso parcial de un producto agrupado.
exl-id: fca6f502-e224-4444-b0d0-f823853c9458
feature: Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-49392: El estado del pedido cambia a cerrado después del reembolso parcial

El parche ACSD-49392 corrige el problema en el que el estado del pedido cambia a cerrado después de un reembolso parcial de un producto agrupado. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.31. El ID del parche es ACSD-49392. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.3.7-p4 y 2.4.1 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El estado del pedido cambia a cerrado después de un reembolso parcial de un producto agrupado.

<u>Pasos a seguir</u>:

1. Inicie sesión en Adobe Commerce y cree cualquier producto agrupado o utilice el producto agrupado existente.
1. Realice un pedido con este producto agrupado con una cantidad mayor que 1.
1. Vaya a la administración y abra el pedido creado en el paso 2 desde **[!UICONTROL Sales]** > **[!UICONTROL Order]** y cree una factura. Observe el estado del pedido. Estará en proceso.
1. Crear un abono parcial (no reembolsar todos los productos del paquete).
1. Compruebe el estado del pedido.

<u>Resultados esperados</u>

Después de crear una nota de abono parcial para el producto agrupado, el estado del pedido está en procesamiento.

<u>Resultados reales</u>

Después de crear una nota de abono parcial para el producto agrupado, se completa el estado del pedido.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
