---
title: "Información general:  [!DNL Quality Patches Tool] (QPT) v1.0.13"
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.0.13.
exl-id: c25d2926-2137-4a55-abb2-8c0cbff184c9
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Información general de [!DNL Quality Patches Tool] (QPT) v1.0.13

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.0.13.

QPT v1.0.13 incluye los siguientes parches:

1. **MCP-87**: Se mejoró el tiempo de indexación de productos de categoría y de indexadores de acciones para perfiles grandes.
1. **MDVA-13203**: corrige el problema en el que el error *tabla search_tmp_* de infracción de restricción de integridad aparece después de un reíndice completo.
1. **MDVA-19391**: corrige el problema en el cual `analytics_collect_data` está generando un error debido a registros de descripción NULL en la tabla `catalog_category_entity_text`.
1. **MDVA-20376**: corrige el problema con el error *No existe esa entidad con customerId = 1* en el error `exception.log` para clientes que iniciaron sesión después de realizar un pedido.
1. **MDVA-22150**: corrige el problema en el cual los clientes con un producto configurable en el carro de compras y un cupón aplicado no pueden iniciar sesión si ese producto configurable está deshabilitado en el administrador.
1. **MDVA-23426**: corrige el problema por el cual los correos electrónicos de notificación enviados por Adobe Commerce contienen un cuerpo en blanco con contenido que se agrega como datos adjuntos.
1. **MDVA-23764**: corrige el error en `JsFooterPlugin.php` que afecta a la visualización de bloques dinámicos.
1. **MDVA-30858**: corrige el problema con los informes de liquidación [!DNL PayPal] que no están disponibles en **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL PayPal]** según lo esperado.
1. **MDVA-32545**: corrige el problema en el cual las facturas no se envían automáticamente al crear pedidos desde el administrador.
1. **MDVA-32714**: corrige el problema por el que el precio de grupo de clientes no funciona en la consulta de productos de GraphQL.
1. **MDVA-33106**: corrige el problema en el que los cambios de producto reprogramados se borran después de ejecutar el comando cron `run`.

Utilice el menú de la izquierda para navegar a una página específica del parche.
