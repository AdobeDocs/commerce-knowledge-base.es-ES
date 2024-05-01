---
title: 'MDVA-31150: factura sin información de crédito de la tienda'
description: El parche MDVA-31150 corrige el problema en el que se crea una factura sin información de crédito de tienda. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8. Tenga en cuenta que el problema se solucionará en la versión 2.4.2 de Adobe Commerce.
exl-id: 70c87b67-6449-4285-9679-cca81613aa72
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-31150: factura sin información de crédito de tienda

El parche MDVA-31150 corrige el problema en el que se crea una factura sin información de crédito de tienda. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8 está instalado. Tenga en cuenta que el problema se solucionará en la versión 2.4.2 de Adobe Commerce.

## Productos y versiones afectados

* Este parche se ha diseñado para Adobe Commerce en la infraestructura en la nube 2.3.5-p2.
* El parche también es compatible con Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.0 a 2.3.5-p2, y 2.4.0 a 2.4.0-p1.

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Después del pedido de factura por API, la información del saldo del cliente y la tarjeta regalo usados no están presentes en la factura.

<u>Pasos a seguir</u>

1. Agregar un importe de crédito de tienda a una cuenta de cliente: en la barra lateral de administración, vaya a **Clientes** > **Todos los clientes.**
1. Busque el registro de cliente y haga clic en **Editar** en la columna Acción, **Crédito de tienda** > Actualizar el saldo > **Guardar cliente**.
1. Vaya a Tienda y añada productos al carro de compras.
1. Realice un pedido aplicando el importe de la tarjeta de regalo o de crédito de la tienda como pago parcial.
1. Crear factura utilizando `REST API>POST>/rest/V1/order/1/invoice` con carga útil:    ```    { "capture": true, "items": [ { "extension_attributes": {}, "order_item_id": 3, "qty": 1 } ], "notify": true, "appendComment": true, "comment": { "extension_attributes": {}, "comment": "string", "is_visible_on_front": 0 }, "arguments": { "extension_attributes": {} }}    ```
1. Obtener la factura que se acaba de crear con `REST API>GET>/rest/V1/invoices/1`.

<u>Resultado esperado</u>

El saldo de la tarjeta de regalo y el crédito de la tienda se devuelven mediante una llamada API.

<u>Resultado real</u>

El saldo de la tarjeta de regalo y el crédito de la tienda no se devuelven mediante una llamada API.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
