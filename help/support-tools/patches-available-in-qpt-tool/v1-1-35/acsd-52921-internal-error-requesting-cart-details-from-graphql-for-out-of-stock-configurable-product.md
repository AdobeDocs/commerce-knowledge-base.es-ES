---
title: "ACSD-52921: Error al solicitar los detalles del carro de compras de GraphQL para un producto configurable sin existencias"
description: Aplique el parche ACSD-52921 para corregir el problema de Adobe Commerce en el que se produce un error interno al solicitar detalles del carro de compras de GraphQL para un producto configurable sin existencias.
feature: GraphQL, Configuration, Products, Shopping Cart
role: Admin
exl-id: 687460c4-f0d5-45d2-82b1-dda2947fe1e7
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-52921: Error al solicitar los detalles del carro de compras de GraphQL para un producto configurable sin existencias

El parche ACSD-52921 corrige el problema en el que se produce un error interno al solicitar detalles del carro de compras de GraphQL para un producto configurable sin existencias. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.35 está instalado. El ID del parche es ACSD-52921. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se produce un error interno al solicitar los detalles del carro de compras de GraphQL para un producto configurable sin existencias.

<u>Pasos a seguir</u>:

1. Cree un producto configurable con algunas opciones.
1. Agregue una opción para el producto configurable anterior al carro de compras desde el front-end (cierre de compra de invitado).
1. Obtenga la `[ masked_id ]` desde el `[ quote_id_mask ]` tabla db para la oferta creada anteriormente.
1. Ejecute la siguiente consulta de GraphQL para obtener los detalles anteriores del carro de compras de invitados.

   Añada el `[ masked_id ]` recibido del paso 3 en la consulta.

   ```GraphQL
   {
       cart(cart_id: "masked_id") {
           items {
               product {
                   name
                   sku
               }
               ... on ConfigurableCartItem {
                   configurable_options {
                       configurable_product_option_uid
                       option_label
                       configurable_product_option_value_uid
                       value_label
                   }
               }
               quantity
               errors {
                   code
                   message
               }
           }
       }
   }   
   ```

1. Esto devolverá los detalles del presupuesto sin ningún problema.
1. Vaya al servidor y actualice el producto configurable de *[!UICONTROL Stock Status]* hasta *[!UICONTROL Out of Stock]*.
1. Ejecute la misma consulta de GraphQL, como se hace en el paso 4.

<u>Resultados esperados</u>:

El mensaje de error se envía o se trata correctamente en la respuesta.

<u>Resultados reales</u>:

*500 Servidor interno* se genera un error como respuesta a la consulta de GraphQL.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
