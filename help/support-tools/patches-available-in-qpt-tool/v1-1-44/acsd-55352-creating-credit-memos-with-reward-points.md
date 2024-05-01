---
title: "ACSD-55352: Creación de notas de crédito con puntos de recompensa"
description: Aplique el parche ACSD-55352 para solucionar el problema de Adobe Commerce en el que, después de crear una nota de crédito parcial con puntos de recompensa del cliente, el estado del pedido cambia a *cerrado* y las opciones de nota de crédito desaparecen de la página de orden del administrador.
feature: Checkout, Orders
role: Admin, Developer
exl-id: 33ceb2e9-3cd5-4472-941a-e06c5c534f4a
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# ACSD-55352: Creación de notas de crédito con puntos de recompensa

El parche ACSD-55352 soluciona el problema por el que, después de crear una nota de crédito parcial con puntos de recompensa del cliente, el estado de la orden cambia a *cerrado* Las opciones de nota de crédito y de descargo desaparecen de la página de orden de administración. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 está instalado. El ID del parche es ACSD-55352. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Después de crear una nota de crédito parcial con puntos de recompensa del cliente, el estado del pedido cambia a *cerrado* Las opciones de nota de crédito y de descargo desaparecen de la página de orden de administración.

<u>Pasos a seguir</u>:

1. Inicie sesión en el administrador de Adobe Commerce.
2. Ir a **[!UICONTROL Stores]** > **[!UICONTROL Other Setting]** > **[!UICONTROL Reward Exchange Rates]** > **[!UICONTROL Add New Rate]**.
3. Añada dos tarifas:
   * *[!UICONTROL First]*:
      * *[!UICONTROL Direction]* = *Puntos por moneda*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
   * *[!UICONTROL Second]*:
      * *[!UICONTROL Direction]* = *Moneda a puntos*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
4. Crear un producto sencillo con el precio de *100 $* y con *Cant* : *100*.
5. Cree un cliente desde la tienda.
6. Vaya al servidor de nuevo: **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit]** > **[!UICONTROL Reward Points]** > **[!UICONTROL Update Points]** > Agregar *100* y guarde al cliente.
7. Vaya a la tienda e inicie sesión como el cliente creado anteriormente.
8. Añadir el producto al carro de compras con *Cant* : *10*.
9. Ir a **[!UICONTROL Checkout]** y utilice el disponible *100* recompense los puntos cuando se le solicite y realice el pedido.
10. Ir a **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice]** y enviar esa orden.
11. Ir a [!UICONTROL Credit Memo] y actualice el *Cantidad a reembolsar* hasta *8*.
12. Marque la **[!UICONTROL Refund Reward Points]** y haga clic en **[!UICONTROL Refund offline]**.
13. Trate de reembolsar los otros dos productos restantes del pedido, utilizando el [!UICONTROL Credit Memo].

<u>Resultados esperados</u>:

* El administrador crea [!UICONTROL Credit Memo] para devolver los dos productos restantes.
* El estado del pedido es *Completado*.

<u>Resultados reales</u>:

* No se pueden crear más [!UICONTROL Credit Memo].
* El estado del pedido es *Cerrado*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
