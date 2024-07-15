---
title: "parche de MDVA-33281: problemas de incoherencia de inventario"
description: El parche MDVA-33281 soluciona tres problemas de incoherencia de inventario. Haga clic en los problemas vinculados en la sección Problema para ver los pasos para reproducir estos errores. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14.
exl-id: adba9728-6e42-467e-943d-cf8af0bec353
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# Parche MDVA-33281: problemas de incoherencia de inventario

El parche MDVA-33281 soluciona tres problemas de incoherencia de inventario. Haga clic en los problemas vinculados en la sección Problema para ver los pasos para reproducir estos errores. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.5-p1

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El parche corrige problemas de incoherencia del inventario como:

* **Error grave de PHP** al ejecutar `bin/magento inventory:reservation:list-inconsistencies` en la CLI debido a un tipo de parámetro de SKU incorrecto.
* **Duplicar datos** en la lista de incoherencias.
* **Se creará una nueva reserva** antes de realizar el pedido (realización anterior basada en la reserva después de realizar el pedido). En caso de errores en la realización del pedido, se añadirá una reserva adicional para compensar.

>[!NOTE]
>
>También hay un parche MDVA-30112 que resuelve el problema donde hay un número inesperadamente grande de [incoherencias en la reserva](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) en nuestra documentación para desarrolladores, en la tabla `inventory_reservation`. Para obtener la solución, consulte [parche del Magento MDVA-30112: gran número de incoherencias en las reservas](/help/support-tools/patches-available-in-qpt-tool/v1-0-8/mdva-30112-magento-patch-large-number-reservation-inconsistencies.md) en nuestra base de conocimiento de asistencia.

## Error grave de PHP

<u>Pasos a seguir</u>:

Error grave de PHP al ejecutar `bin/magento inventory:reservation:list-inconsistencies`.

Para obtener una lista de incoherencias en la reserva, inicie sesión en el servidor de producción y ejecute el siguiente comando en la CLI (conmutador-r: salida sin procesar):

<pre>inventario bin/magento:reservation:list-inconsistencies -r</pre>

<u>Resultados esperados</u>:

Se crea la lista de incoherencias de la reserva. Se devolverán en el siguiente formato

```plaintext
<ORDER_INCREMENT_ID>:<SKU>:<QUANTITY>:<STOCK-ID>
```

<u>Resultados reales</u>:

Se genera un error grave de PHP.

## Duplicar datos

Los datos duplicados están en `inventory_reservation table`.

<u>Pasos a seguir</u>:

Para solucionar las incoherencias en las reservas, ejecute el siguiente comando:

<pre>SELECCIONAR *, RECUENTO(*)
DESDE inventory_reservation
AGRUPAR POR metadatos, SKU, cantidad
HAVING COUNT(*) &gt; 1</pre>

<u>Resultados esperados</u>:

No hay duplicados.

<u>Resultados reales</u>:

Hay duplicados.

## Nueva reserva

<u>Pasos a seguir</u>:

Nueva reserva creada antes de realizar el pedido:

1. Importe la base de datos.
1. Ejecute `bin/magento setup:upgrade` en el terminal.
1. Enumerar incoherencias ejecutando `bin/magento inventory:reservation:list-inconsistencies        -i -r` en el terminal.

<u>Resultados esperados</u>:

Sin bucle y resultados mucho más rápidos.

<u>Resultados reales</u>:

Los mismos resultados se muestran en un bucle infinito o el comando falla con `memory_limit`, según la configuración del sistema.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
