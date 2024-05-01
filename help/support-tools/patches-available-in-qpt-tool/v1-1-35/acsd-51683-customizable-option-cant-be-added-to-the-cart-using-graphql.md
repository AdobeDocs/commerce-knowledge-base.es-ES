---
title: "ACSD-51683: La opción personalizable no se puede añadir al carro de compras con GraphQL"
description: Aplique el parche ACSD-51683 para solucionar el problema de Adobe Commerce en el que la opción personalizable no se puede añadir al carro de compras con GraphQL.
feature: GraphQL
role: Admin
exl-id: 4de0d8b7-714e-4bbf-8a0d-bb6e0c3aae55
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-51683: La opción personalizable no se puede añadir al carro de compras con GraphQL

El parche ACSD-51683 corrige el problema en el que la opción personalizable no se puede añadir al carro de compras con GraphQL. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 está instalado. El ID del parche es ACSD-51683. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La opción personalizable no se puede añadir al carro de compras con GraphQL.

<u>Pasos a seguir</u>:

1. Cree un producto sencillo con un personalizable **Campo de texto** opción.
1. [Añadir al carro de compras](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/add-product-to-cart/) Seleccione el producto creado con la opción personalizable requerida mediante GraphQL.
1. Envíe el [carrito](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/queries/cart/) Solicitud de GraphQL para comprobar el producto y sus detalles en el carro de compras.

<u>Resultados esperados</u>

El `Customizable_options` de la respuesta de GraphQL contiene los datos proporcionados al añadir el producto al carro de compras.

<u>Resultados reales</u>

El `Customizable_options` La sección de la respuesta de GraphQL está vacía.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
