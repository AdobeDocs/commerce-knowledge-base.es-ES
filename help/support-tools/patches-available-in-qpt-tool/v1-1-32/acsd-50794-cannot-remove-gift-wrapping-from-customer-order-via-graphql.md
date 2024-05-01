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

El parche ACSD-50794 corrige el problema en el que los usuarios no pueden eliminar el envoltorio para regalos del pedido del cliente a través de GraphQL. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 está instalado. El ID del parche es ACSD-50794. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios no pueden eliminar el envoltorio para regalos del pedido del cliente a través de GraphQL.

<u>Pasos a seguir</u>:

1. Cree un cliente desde el front-end.
1. Cree un producto sencillo.
1. Activar *[!UICONTROL Gift Messages]* al ir a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Options]** y establecer *[!UICONTROL Allow Gift Messages]* = *[!UICONTROL Yes]*.
1. Crear *[!UICONTROL Gift Wrapping]* al ir a **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Gift Wrapping]**.
1. Obtener token de cliente.
1. Cree un carro de compras vacío, customerCart.
   * Añadir productos al carro de compras: `addProductsToCart` mutación
   * Establecer dirección de facturación: `setBillingAddressOnCart` mutación
   * Establecer dirección de envío: `setShippingAddressesOnCart` mutación
   * Definir método de envío: `setShippingMethodsOnCart` mutación (plana)
   * Definir forma de pago: `setPaymentMethodOnCart` mutación (checkmo)
1. Ahora revisa el envoltorio para regalos *Uid* con esta consulta del carro de compras:

   <pre><code class="language-GraphQL">
    {
      cart(cart_id: "{{CART_ID}}") {
        available_gift_wrappings{
            uid
        }
    }
    }
    </code></pre>

1. Configurar el envoltorio para regalos mediante `setGiftOptionsOnCart`.
1. Marque la consulta cart: cart.
1. Anular ajuste de regalo usando `setGiftOptionsOnCart` (establezca el valor en null).
1. De nuevo, compruebe la consulta cart: cart.
1. Realizar pedido: `placeOrder` mutación.
1. Ejecutar consulta del cliente: cliente.

   <pre><code class="language-graphql">
    query {
      customer {
        firstname
        middlename
        lastname
        suffix
        email
        orders {
            items {
                order_date
                gift_wrapping {
                    design
                    uid
                }
            }
        }
        addresses {
          firstname
          middlename
          lastname
          street
          city
          region {
            region_code
            region
          }
          postcode
          country_code
          telephone
        }
      }
    }
    </code></pre>

<u>Resultados esperados</u>:

Una vez que un usuario establece un envoltorio para regalos y lo anula, la consulta del cliente devuelve un valor nulo.

<u>Resultados reales</u>:

La consulta del cliente sigue devolviendo el envoltorio para regalos según se aplica.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
