---
title: "ACSD-50794: No se puede eliminar el envoltorio para regalos del pedido del cliente a través de GraphQL"
description: Aplique el parche ACSD-50794 para solucionar el problema de Adobe Commerce en el que los usuarios no pueden eliminar el envoltorio para regalos del pedido del cliente a través de GraphQL.
exl-id: 4983910c-9ea0-451e-a2b6-81485184bbce
feature: Gift, GraphQL, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-50794: no se puede eliminar el envoltorio para regalos del pedido del cliente mediante GraphQL

El parche ACSD-50794 corrige el problema en el que los usuarios no pueden eliminar el envoltorio para regalos del pedido del cliente a través de GraphQL. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32. El ID del parche es ACSD-50794. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios no pueden eliminar el envoltorio para regalos del pedido del cliente a través de GraphQL.

<u>Pasos a seguir</u>:

1. Cree un cliente desde el front-end.
1. Cree un producto sencillo.
1. Habilite *[!UICONTROL Gift Messages]* yendo a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Options]** y establezca *[!UICONTROL Allow Gift Messages]* = *[!UICONTROL Yes]*.
1. Cree *[!UICONTROL Gift Wrapping]* yendo a **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Gift Wrapping]**.
1. Obtener token de cliente.
1. Cree un carro de compras vacío, customerCart.
   * Agregar productos al carro de compras: `addProductsToCart` mutación
   * Establecer dirección de facturación: `setBillingAddressOnCart` mutación
   * Establecer dirección de envío: `setShippingAddressesOnCart` mutación
   * Definir método de envío: mutación `setShippingMethodsOnCart` (tasa plana)
   * Establecer método de pago: `setPaymentMethodOnCart` mutación (checkmo)
1. Ahora revise el envoltorio para regalos *Uid* con esta consulta del carro de compras:

   <pre><code class="language-GraphQL">
    &lbrace;
      cart(cart_id: "{{CART_ID}}") &lbrace;
        available_gift_wrappings&lbrace;
            uid
        &rbrace;
    &rbrace;
    &rbrace;
    </code></pre>

1. Definir envoltorio para regalos con `setGiftOptionsOnCart`.
1. Marque la consulta cart: cart.
1. Anule el ajuste de regalo mediante `setGiftOptionsOnCart` (establezca el valor en null).
1. De nuevo, compruebe la consulta cart: cart.
1. Orden: `placeOrder` mutación.
1. Ejecutar consulta del cliente: cliente.

   <pre><code class="language-graphql">
    query &lbrace;
      customer &lbrace;
        firstname
        middlename
        lastname
        suffix
        email
        orders &lbrace;
            items &lbrace;
                order_date
                gift_wrapping &lbrace;
                    design
                    uid
                &rbrace;
            &rbrace;
        &rbrace;
        addresses &lbrace;
          firstname
          middlename
          lastname
          street
          city
          region &lbrace;
            region_code
            region
          &rbrace;
          postcode
          country_code
          telephone
        &rbrace;
      &rbrace;
    &rbrace;
    </code></pre>

<u>Resultados esperados</u>:

Una vez que un usuario establece un envoltorio para regalos y lo anula, la consulta del cliente devuelve un valor nulo.

<u>Resultados reales</u>:

La consulta del cliente sigue devolviendo el envoltorio para regalos según se aplica.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
