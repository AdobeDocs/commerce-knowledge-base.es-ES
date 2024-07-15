---
title: "MDVA-30112: gran número de incoherencias en la reserva"
description: El parche MDVA-30112 resuelve el problema de que hay un número inesperadamente elevado de [incoherencias en la reserva](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) en la tabla "inventory_reservation". Las incoherencias en las reservas incluyen pedidos abiertos no registrados y pedidos completos que no están registrados. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8. Tenga en cuenta que el problema se corrigió en la versión 2.4.2 de Adobe Commerce.
exl-id: db74fb61-dfeb-4e99-8513-d36fd68d2267
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# MDVA-30112: gran número de incoherencias en la reserva

El parche MDVA-30112 resuelve el problema que presenta un número inesperadamente elevado de [incoherencias en la reserva](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) en la tabla `inventory_reservation`. Las incoherencias en las reservas incluyen pedidos abiertos no registrados y pedidos completos que no están registrados. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8. Tenga en cuenta que el problema se corrigió en la versión 2.4.2 de Adobe Commerce.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce en infraestructura en la nube 2.3.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.4 - 2.3.5-p2, 2.4.0 - 2.4.1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El valor [tamaño de grupo](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#list-inconsistencies-command) es el valor de cuántos pedidos se cargarán a la vez. Cuando hay más pedidos que este valor, Adobe Commerce considera que los pedidos con estado pendiente son incoherencias.

>[!NOTE]
>
>Hay un parche MDVA-33281 que corrige otros tres problemas de inconsistencia de inventario. Esto incluye un error grave de PHP al ejecutar `bin/magento inventory:reservation:list-inconsistencies` en la CLI. Otro problema que se corrige son los datos duplicados en la lista de incoherencias. Además, el problema en el que se crea una reserva antes de realizar el pedido (realización anterior basada en la reserva después de realizar el pedido). Para obtener la solución, consulte [MDVA-33281: problemas de incoherencia de inventario](/help/support-tools/patches-available-in-qpt-tool/v1-0-14/mdva-33281-magento-patch-inventory-inconsistency-issues.md) en nuestra base de conocimiento de soporte.

<u>Requisitos previos</u>:

Ejecute el siguiente comando en la CLI para enumerar las incoherencias en la reserva en la tabla `inventory_reservation`:

```
magento inventory:reservation:list-inconsistencies
```

Verá un número inesperadamente alto de incoherencias en la reserva o el comando nunca se completa.

<u>Pasos a seguir</u>:

1. Ejecute el siguiente comando en la CLI para resolver las incoherencias:

   ```
   bin/magento inventory:reservation:list-inconsistencies -r | bin/magento inventory:reservation:create-compensations
   ```

1. Realice tres pedidos:
   * Asigne a cada uno un solo producto.
   * Utilice el método de pago Cheque/Giro Postal, por lo que el estado del pedido será &quot;pendiente&quot;.
1. Se pueden ver tres registros con -1 cantidad en la tabla `inventory_reservation`. Ejecute el siguiente comando en la CLI para ver cualquier incoherencia:

   ```
   bin/magento inventory:reservation:list-inconsistencies
   ```

   Esto no devuelve resultados, lo que es correcto.

1. Ejecute el siguiente comando en la CLI:

   ```
   Execute bin/magento inventory:reservation:list-inconsistencies      --bunch-size 1
   ```

   Verá que las solicitudes de estado &quot;pendientes&quot; se muestran como incoherencias.

1. Ejecute el siguiente comando en la CLI:

   ```
   bin/magento inventory:reservation:list-inconsistencies      -r --bunch-size 1 | bin/magento inventory:reservation:create-compensations
   ```

<u>Resultados esperados</u>:

Adobe Commerce no debe resolver las incoherencias de las solicitudes de estado &quot;pendientes&quot;. Las incoherencias en las existencias deben resolverse para pedidos con estados &quot;completo&quot;, &quot;cerrado&quot; y &quot;cancelado&quot;.

<u>Resultados reales</u>:

Cuando hay pedidos que superan el valor de tamaño de grupo especificado, Adobe Commerce considera los pedidos con estado &quot;pendiente&quot; como incoherencias y agrega varios registros de resolución de incoherencias para el mismo pedido.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
