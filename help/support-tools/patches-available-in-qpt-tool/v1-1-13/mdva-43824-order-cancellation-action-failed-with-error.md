---
title: '''MDVA-43824: la acción de cancelación del pedido falló con el error "No ha cancelado el artículo"'
description: '''El parche de MDVA-43824 resuelve el problema en el que la acción de cancelación del pedido falló con el error: *No ha cancelado el elemento*. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. El ID del parche es MDVA-43824. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5."'
exl-id: e4d839d6-84ed-4157-80a1-fd482fef897c
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-43824: La acción de cancelación del pedido falló con el error &quot;No ha cancelado el artículo&quot;

El parche MDVA-43824 resuelve el problema en el que la acción de cancelación de la solicitud fallaba con el siguiente error: *No has cancelado el artículo*. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 está instalado. El ID del parche es MDVA-43824. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.6 - 2.3.7-p3, 2.4.1 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

No se puede cancelar el pedido realizado por un cliente que ha iniciado sesión. Error en la acción de cancelación del pedido:

```
Zend_Db_Statement_Exception: SQLSTATE[23000]: Integrity constraint violation: 1452 Cannot add or update a child row: a foreign key constraint fails (`mer33515_ee24developpbdevelop`.`salesrule_customer`, CONSTRAINT `SALESRULE_CUSTOMER_RULE_ID_SEQUENCE_SALESRULE_SEQUENCE_VALUE` FOREIGN KEY (`rule_id`) REFERENCES `sequence_salesrule` (`sequen), query was: INSERT INTO `salesrule_customer` () VALUES (){code}
```

<u>Pasos a seguir</u>:

1. Cree una regla de ventas (el tipo de cupón es &quot;Cupón específico&quot; o &quot;Sin cupón&quot;).
1. Vaya a la tienda, inicie sesión como cliente y añada un producto al carro de compras.
1. Vaya al carro de compras y aplique la regla de precio si la regla tiene un cupón como &quot;Cupón específico&quot;. La regla de precios del carro de compras debe aplicarse correctamente.
1. Vaya a Pago y envío y haga el pedido con cualquier forma de pago.
1. Vaya a Commerce > Administración > **Ventas** > **Pedidos**.
1. Abra el pedido realizado en el paso 4.
1. Haga clic en **Cancelar** botón.

<u>Resultados esperados</u>:

El pedido se cancela correctamente sin ningún error.

<u>Resultados reales</u>:

Error en la acción de cancelación del pedido: *No has cancelado el artículo.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
