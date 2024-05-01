---
title: 'Información general: [!DNL Quality Patches Tool] (QPT) v1.0.13'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.0.13.
exl-id: c25d2926-2137-4a55-abb2-8c0cbff184c9
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] Información general de (QPT) v1.0.13

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.0.13.

QPT v1.0.13 incluye los siguientes parches:

1. **MCP-87**: Se ha mejorado el tiempo de indexación para los indexadores de productos de categoría y de existencias para perfiles grandes.
1. **MDVA-13203**: corrige el problema en el que las variables *Infracción de restricción de integridad search_tmp_ table* El error aparece después de una reindexación completa.
1. **MDVA-19391**: soluciona el problema donde `analytics_collect_data` está generando un error debido a registros de descripción NULL en la `catalog_category_entity_text` tabla.
1. **MDVA-20376**: soluciona el problema con *No existe esa entidad con customerId = 1* error en `exception.log` para clientes que iniciaron sesión después de realizar el pedido.
1. **MDVA-22150**: corrige el problema en el cual los clientes con un producto configurable en el carro de compras y un cupón aplicado no pueden iniciar sesión si ese producto configurable está deshabilitado en el Administrador.
1. **MDVA-23426**: corrige el problema en el cual los correos electrónicos de notificación enviados por Adobe Commerce contienen un cuerpo en blanco con contenido que se agrega como archivo adjunto.
1. **MDVA-23764**: corrige el error en `JsFooterPlugin.php` que afecta a la visualización de bloques dinámicos.
1. **MDVA-30858**: soluciona el problema con [!DNL PayPal] Los informes de liquidación no están disponibles en **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL PayPal]** Liquidación según lo esperado.
1. **MDVA-32545**: corrige el problema en el que las facturas no se envían automáticamente al crear pedidos desde el administrador.
1. **MDVA-32714**: corrige el problema en el que el precio de grupo de clientes no funciona en la consulta de productos de GraphQL.
1. **MDVA-33106**: corrige el problema en el que los cambios reprogramados del producto se borran después de la activación `run` se ejecuta el comando.

Utilice el menú de la izquierda para navegar a una página específica del parche.
