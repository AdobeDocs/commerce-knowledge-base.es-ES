---
title: "ACSD-51819: realización de varios pedidos con un solo ID de oferta"
description: Aplique el parche ACSD-51819 para solucionar el problema de Adobe Commerce, en el que se pueden realizar varios pedidos a través del mismo ID de oferta.
feature: Orders, Checkout
role: Admin, Developer
exl-id: f217de21-2914-4b84-b596-e9e763669941
source-git-commit: 6fa7182a807147a00ad750966cd839ec18ffe0c7
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51819: realización de varios pedidos con un solo ID de oferta

El parche ACSD-51819 corrige el problema en el que se pueden realizar varios pedidos a través del mismo ID de presupuesto. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 está instalado. El ID del parche es ACSD-51819. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se pueden realizar varios pedidos con el mismo ID de oferta.

<u>Pasos a seguir</u>:

1. Inicie sesión como usuario.
1. Agregue elementos al carro de compras y continúe con el cierre de compra.
1. Elija cualquier forma de pago, pero no haga clic en **[!UICONTROL Place Order]** botón.
1. Inicie sesión en la misma cuenta en otro explorador.
1. Continúe con el cierre de compra con los mismos elementos sin hacer clic en **[!UICONTROL Place Order]** botón.
1. Haga clic en **[!UICONTROL Place Order]** en ambos sistemas al mismo tiempo.
1. Valide los pedidos realizados en ambos exploradores.

<u>Resultados esperados</u>:

Solo se procesa correctamente el primer pedido realizado desde un explorador.

<u>Resultados reales</u>:

Los pedidos se han realizado en ambos navegadores.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
