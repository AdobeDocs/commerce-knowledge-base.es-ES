---
title: "ACSD-49433: Cantidad predeterminada que se muestra como subtotal en el carro de compras para la tarjeta de regalo"
description: Aplique el parche ACSD-49433 para corregir el problema de Adobe Commerce en el que la cantidad predeterminada se muestra como subtotal en el carro de compras para la tarjeta regalo con una cantidad abierta.
exl-id: e2a887bb-c15a-43a6-a145-b295deef399b
feature: Admin Workspace, Gift, Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-49433: cantidad predeterminada que se muestra como subtotal en el carro de compras para la tarjeta de regalo

El parche ACSD-49433 corrige el problema en el que la cantidad predeterminada se muestra como subtotal en el carro de compras de la tarjeta regalo con una cantidad abierta. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 está instalado. El ID del parche es ACSD-49433. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La cantidad predeterminada se muestra como subtotal en el carro de compras para la tarjeta de regalo con una cantidad abierta.

<u>Pasos a seguir</u>:

1. Cree una tarjeta regalo.
1. Asegúrese de que la cantidad abierta está configurada en *[!UICONTROL Yes]* (entre 50 y 500 dólares).
1. Vaya a la [!UICONTROL Gift Card] producto en la tienda y elige otra cantidad de la lista desplegable.
1. Especifique 100 $ en la cantidad en USD.
1. Rellene otros campos y agréguelos al carro de compras.
1. Vaya a la página del minicarrito o del carrito.

<u>Resultados esperados</u>:

El subtotal muestra la cantidad que el usuario ingresó.

<u>Resultados reales</u>:

El subtotal muestra la cantidad predeterminada de la tarjeta regalo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
