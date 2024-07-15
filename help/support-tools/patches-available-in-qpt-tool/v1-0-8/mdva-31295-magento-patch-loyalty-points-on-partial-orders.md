---
title: "MDVA-31295: Puntos de fidelidad en pedidos parciales"
description: El parche MDVA-31295 soluciona el problema de que los puntos de recompensa no se calculan correctamente cuando se completa un pedido parcial y los artículos se gravan. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.
exl-id: 10e8a3a9-bfab-4256-b772-fd64e8885da3
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-31295: Puntos de fidelización en pedidos parciales

El parche MDVA-31295 soluciona el problema de que los puntos de recompensa no se calculan correctamente cuando se completa un pedido parcial y los artículos se gravan. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce local 2.3.0

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las recompensas no se aplican a las cuentas de los clientes cuando se completa el pedido (se envía parcialmente) y los artículos se gravan. Cuando los artículos no están gravados, las recompensas se añaden correctamente a las cuentas de los clientes.

<u>Pasos a seguir</u>:

1. Inicie sesión en la tienda como cliente.
1. Agregue dos productos al carro de compras.
1. Vaya a Pago y envío, establezca la dirección de envío que tiene impuestos y realice el pedido.
1. En el administrador, vaya al pedido realizado recientemente.
1. Haga clic en **Factura**, establezca **Cantidad en Factura** en 0 para uno de los artículos y haga clic en **Actualizar cantidad**. Enviar factura.
1. Haga clic en Enviar y establezca **Cant. a enviar** en 0 para el artículo que no se facturó. Haz clic en **Enviar envío**.
1. Haga clic en Cancelar pedido. El estado se establecerá como Completo.
1. En el administrador, vaya a **Clientes** > Elija la compra del cliente realizada antes > **Puntos de recompensa** > **Historial de puntos de recompensa**.
1. Compruebe los puntos de recompensa obtenidos por el pedido realizado.

<u>Resultados esperados</u>:

Los puntos de recompensa deben calcularse para las órdenes gravables cuando finaliza una orden parcial.

<u>Resultados reales</u>:

Los puntos de recompensa no se calculan para una orden imponible cuando finaliza una orden parcial.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
