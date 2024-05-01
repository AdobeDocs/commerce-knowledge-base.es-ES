---
title: "MDVA-28300: problema de cálculo de precios con la regla de precios de catálogo en GraphQL"
description: El parche MDVA-28300 corrige el problema en el que la solicitud de GraphQL no refleja los cambios de precio de las reglas de precios de catálogo. Este parche está disponible cuando está instalada la herramienta Parches de calidad (QPT) v.1.0.6. Tenga en cuenta que el problema se corrigió en la versión 2.3.6 de Adobe Commerce.
exl-id: 86079d29-db69-4758-a159-aeed8e0ea21f
feature: Catalog Management, GraphQL, Customer Service, Marketing Tools, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---

# MDVA-28300: problema de cálculo de precios con la regla de precios de catálogo en GraphQL

>[!WARNING]
>
>Un nuevo parche llamado MDVA-33975 soluciona los problemas de cálculo de precios de GraphQL. MDVA-28300 está depreciado y se recomienda aplicar el parche MDVA-33975. Para acceder a este parche, consulte [MDVA-33975: cálculos de precios de GraphQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html).

El parche MDVA-28300 corrige el problema en el que la solicitud de GraphQL no refleja los cambios de precio de las reglas de precios de catálogo. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6 está instalado. Tenga en cuenta que el problema se corrigió en la versión 2.3.6 de Adobe Commerce.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:** Adobe Commerce local 2.3.5-p1

**Compatible con las versiones de Adobe Commerce:** Adobe Commerce on-premise y Adobe Commerce en la infraestructura en la nube 2.3.0 - 2.3.5-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando se aplica una regla de precios de catálogo a un grupo de clientes determinado, los precios de los artículos del carro de compras y el total del pedido no se calculan correctamente en GraphQL.

<u>Pasos a seguir:</u>

1. Cree una nueva cuenta de cliente y cambie su grupo de clientes a Venta al por mayor.
1. Creación de una nueva regla de catálogo en **Marketing** > **Promociones** > **Reglas de precio de catálogo** con los siguientes parámetros:
   * Grupos de clientes: WholesaleActions:
   * Aplicar: *Aplicar como porcentaje del original*
   * Descuento: *50*


1. Cree un nuevo producto con precio=100.
1. Inicie sesión en el front-end mediante la cuenta de cliente creada anteriormente (si ya había iniciado sesión, cierre la sesión y vuelva a iniciarla).
1. Añadir el producto al carro de compras. El precio del producto es 50 (precio normal 100) y Total de pedido: 55 (50 + 5 del coste de envío).
1. Ejecute la llamada de API de GraphQL que se describe en [consulta customerCart](https://devdocs.magento.com/guides/v2.3/graphql/queries/customer-cart.html) en nuestra documentación para desarrolladores.

<u>Resultado esperado:</u>

Tanto la API como el front-end tienen el mismo total de pedido con el descuento introducido por la regla de catálogo que se aplica.

<u>Resultado real:</u>

El total del pedido no aplica el descuento de la regla de catálogo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Aplicación de parches mediante la herramienta Parches de calidad](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html).

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la sección Parches disponibles en QPT.
