---
title: "Parche MDVA-32714: el precio de grupo de clientes no funciona a través de GraphQL"
description: El parche MDVA-32714 corrige el problema en el que el precio с grupo de clientes no se añade en la respuesta a la consulta del producto de GraphQL. Este parche está disponible cuando está instalada la herramienta Parches de calidad (QPT) 1.0.13. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.
exl-id: a4fc92ad-68dc-437d-8577-303007ef8a92
feature: GraphQL, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Parche de MDVA-32714: el precio de grupo de clientes no funciona mediante GraphQL

>[!WARNING]
>
>Un nuevo parche llamado MDVA-33975 soluciona los problemas de cálculo de precios de GraphQL. MDVA-32714 está depreciado y se recomienda aplicar el parche MDVA-33975. Para acceder a este parche, consulte [Parche MDVA-33975: cálculos de precios de GraphQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html) en nuestra base de conocimiento de soporte.

El parche MDVA-32714 corrige el problema en el que el precio с grupo de clientes no se añade en la respuesta a la consulta del producto de GraphQL. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 está instalado. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.4.0

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.4 - 2.4.0-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El precio de grupo de clientes para el cliente general no se agrega en la respuesta de consulta de productos de GraphQL.

<u>Pasos a seguir</u>:

1. Habilite y establezca un precio especial para cualquier producto de cualquier grupo de clientes.
1. Utilice la consulta de productos en GraphQL para obtener los precios de este producto, tal como se describe en: [Consulta de productos > Consulta de muestra](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html#sample-queries) en nuestra documentación para desarrolladores.

<u>Resultados esperados</u>:

```api
price_range
```

muestra el precio con descuento para clientes generales según lo que se haya definido en el Panel de administración.

<u>Resultados reales</u>:

```api
price_range
```

no muestra el precio con descuento para clientes generales.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
