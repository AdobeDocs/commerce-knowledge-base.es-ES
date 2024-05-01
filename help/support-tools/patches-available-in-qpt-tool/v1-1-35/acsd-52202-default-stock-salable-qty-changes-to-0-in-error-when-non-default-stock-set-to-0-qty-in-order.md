---
title: "ACSD-52202: La cantidad vendible de stock predeterminada cambia a 0 por error cuando las existencias no predeterminadas se establecen en 0 cantidad en orden"
description: Aplique el parche ACSD-52202 para corregir el problema de Adobe Commerce en el que una cantidad vendible de stock predeterminada cambia a 0 por error cuando el stock no predeterminado se establece en 0 en un pedido.
feature: Inventory, Products
role: Admin
exl-id: 8a3b5da4-cf16-41c8-b2d5-b740d638c745
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-52202: La cantidad vendible de stock predeterminada cambia a 0 por error cuando el stock no predeterminado se establece en 0 cantidad en un pedido

El parche ACSD-52202 corrige el problema en el que una cantidad vendible de stock (cantidad) predeterminada cambia a 0 por error cuando el stock no predeterminado se establece en 0 cantidad en un pedido. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.35 está instalado. El ID del parche es ACSD-52202. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La cantidad vendible de stock predeterminada cambia a 0 por error cuando el stock no predeterminado se establece en 0 cantidad en un pedido.

<u>Pasos a seguir</u>:

1. Inicie sesión en [!DNL Admin].
1. Crear **sitio web2**.
1. Crear personalizado **origen2**.
1. Crear personalizado **stock2**.
1. Asigne el **origen2** y **stock2** hasta **sitio web1** y el origen y las existencias predeterminados del sitio web predeterminado.
1. Cree un producto simple y asígnelo **cantidad** = *10* para el origen predeterminado y **cantidad** = *1* para el **origen2** origen.
1. Realice un pedido con **cantidad** = *1* para **sitio web2**.
1. Cree una factura y un envío.
1. Compruebe el producto simple **cantidad vendible**.

<u>Resultados esperados</u>:

El **cantidad vendible** = *10* para **origen2**.

<u>Resultados reales</u>:

El **cantidad vendible** = *0* para ambas fuentes.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
