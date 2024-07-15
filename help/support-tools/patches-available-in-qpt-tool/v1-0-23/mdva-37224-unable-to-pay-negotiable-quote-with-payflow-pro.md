---
title: 'MDVA-37224: No se puede pagar la "cotización negociable" con PayFlow Pro'
description: El parche de MDVA-37224 soluciona el problema cuando los clientes no pueden pagar una **Cotización negociable** con PayFlow Pro de PayPal. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23. El ID del parche es MDVA-37224. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.3 de Adobe Commerce.
exl-id: df75b38d-64c8-46b5-85ff-7606ce1dfd34
feature: B2B, Orders, Payments, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-37224: No se puede pagar una &quot;cotización negociable&quot; con PayFlow Pro

El parche MDVA-37224 soluciona el problema cuando los clientes no pueden pagar un **presupuesto negociable** con PayFlow Pro de PayPal. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23. El ID del parche es MDVA-37224. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

* El parche se ha diseñado para Adobe Commerce en la infraestructura en la nube 2.3.6-p1
* El parche también es compatible con Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.3-2.4.2-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Requisitos previos</u>:

* Adobe Commerce con módulo B2B instalado
* Funcionalidad de empresa habilitada
* **Funcionalidad de presupuesto negociable** habilitada
* Existe un usuario de empresa
* El método de pago PayFlow Pro de PayPal está activado y configurado
* El método de pago PayPal PayFlow Pro está permitido para B2B
* Se han creado 2 productos con diferentes precios

<u>Pasos a seguir</u>:

1. Abra la Tienda.
1. Agregue **Producto 1** al carro de compras.
1. Crear un **presupuesto negociable** para **producto 1**.
1. Agregue **Producto 2** al carro de compras.
1. Desde el administrador, acepte el **presupuesto negociable** creado en el paso 3.
1. Desde la Tienda, abre este **Presupuesto negociable** y continúa con el cierre de compra.
1. Seleccione el **método de pago** = *PayPal PayFlow Pro* en el paso **Revisar y efectuar pagos**.
1. Realice el pedido.

<u>Resultados esperados</u>:

* El pedido se ha realizado correctamente, tal como se esperaba.
* PayPal envía correos electrónicos con la información correcta al cliente, según lo esperado.

<u>Resultados reales</u>:

* La página web se bloquea y no completa el pedido.
* PayPal envía una confirmación al cliente con valores cero, de forma similar a este ejemplo:

```php
Order ID: A1xxxxxxxxx
Order Placed: Monday, April 21, 2021 01:12:12 PM PDT

Shipping Amount: $0.00
Tax Amount: $0.00
Amount of Transaction: $0.00
Payment Type: Visa

BILL TO
--------
US
```


## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* 
   * [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
