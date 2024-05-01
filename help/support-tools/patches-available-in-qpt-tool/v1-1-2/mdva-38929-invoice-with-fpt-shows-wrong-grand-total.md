---
title: "MDVA-38929: La factura con FTP muestra un total incorrecto"
description: El parche MDVA-38929 resuelve el problema en el que la factura con FTP muestra un total general incorrecto cuando el pedido se paga con crédito de tienda. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. El ID del parche es MDVA-38929. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: 1ed0e311-f4a5-4dc0-98fc-fc1cc9458516
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-38929: La factura con FTP muestra un total incorrecto

El parche MDVA-38929 resuelve el problema en el que la factura con FTP muestra un total general incorrecto cuando el pedido se paga con crédito de tienda. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 está instalado. El ID del parche es MDVA-38929. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La factura con FTP muestra un total general incorrecto cuando el pedido se paga con crédito de tienda.

<u>Pasos a seguir</u>:

1. Cree un cliente y asegúrese de que el cliente tiene suficiente crédito de tienda para cubrir el pedido.
1. Habilitar FTP y agregar FTP a un producto.
1. Desde el front-end, inicie sesión como el cliente que acaba de crear.
1. Añada el producto con FTP al carro de compras.
1. Pago y envío y pago con crédito de la tienda. Debería ser una orden de pago cero.
1. Vaya a Pedidos y factura manualmente el pedido.
1. Compruebe el total general de la factura.

<u>Resultados esperados</u>:

* El total general de la factura es cero.
* El importe total pagado del pedido es cero.

<u>Resultados reales</u>:

* El total general de la factura sigue mostrando el importe FTP.
* El total pagado sigue mostrando la cantidad de FTP.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
