---
title: "MDVA-44562: el ID de tienda de los artículos de presupuesto se sobrescribe por el ID de tienda predeterminado"
description: El parche MDVA-44562 corrige el problema en el que el ID de tienda predeterminado anula el ID de tienda de los elementos de presupuesto de las solicitudes de GraphQL. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16. El ID del parche es MDVA-44562. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.
exl-id: 902bfc05-411d-4a6c-a6e8-cd7376629b0c
feature: Quotes
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-44562: el ID de tienda de los artículos de presupuesto se sobrescribe por el ID de tienda predeterminado

El parche MDVA-44562 corrige el problema en el que el ID de tienda predeterminado anula el ID de tienda de los elementos de presupuesto de las solicitudes de GraphQL. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16. El ID del parche es MDVA-44562. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El ID de tienda de los artículos de presupuesto se anula con el ID de tienda predeterminado para las solicitudes de GraphQL.

<u>Pasos a seguir</u>:

1. Crear una nueva vista de tienda.
1. Cree un nuevo producto simple con diferentes nombres por vista de tienda.
1. Crear un cliente nuevo.
1. Obtenga el token de autorización de cliente.

   ```GraphQL
    POST /rest/all/V1/integration/customer/token
    {
      "username": "test@example.com",
      "password": "password"
     }
   ```

1. Cree una nueva cotización para el cliente utilizando el token de autorización.

   ```GraphQL
   POST rest/default/V1/carts/mine
   ```

1. Añadir un producto al carro de compras.

   ```GraphQL
   POST /rest/default/V1/carts/mine/items
   {
     "cartItem": {
       "sku": "simple1",
       "qty": 1,
       "quote_id": "1"
     }
   }
   ```

1. Obtener el contenido del carro de compras para la vista de tienda predeterminada.

   ```GraphQL
   GET rest/default/V1/carts/mine/
   ```

1. Obtener el contenido del carro de compras para la nueva vista de la tienda.

   ```GraphQL
   GET rest/<store_view_2>/V1/carts/mine/
   ```

<u>Resultados esperados</u>:

La respuesta de la vista de la nueva tienda muestra el nombre del producto desde la vista de la nueva tienda.

<u>Resultados reales</u>:

La respuesta de la nueva vista de tienda muestra la configuración del nombre del producto en la vista de tienda predeterminada.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
