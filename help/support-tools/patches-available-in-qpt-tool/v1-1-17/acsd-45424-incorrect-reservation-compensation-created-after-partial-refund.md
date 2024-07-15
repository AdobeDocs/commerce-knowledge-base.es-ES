---
title: "ACSD-45424: Compensación de reserva incorrecta creada después del reembolso parcial"
description: El parche ACSD-45424 corrige el problema en el que se crea una compensación de reserva incorrecta después de un reembolso parcial. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17. El ID del parche es ACSD-45424. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.
exl-id: 0676cfda-a28e-4a66-a75b-8a3fc5e22566
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# ACSD-45424: Compensación de reserva incorrecta creada tras un reembolso parcial

El parche ACSD-45424 corrige el problema en el que se crea una compensación de reserva incorrecta después de un reembolso parcial. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17. El ID del parche es ACSD-45424. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.4 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se crea una compensación de reserva incorrecta después de un reembolso parcial.

<u>Pasos a seguir</u>:

1. Habilitar el método de envío de envío en tienda.
1. Cree tres orígenes de inventario y asegúrese de que la ubicación de recogida esté activa en cada uno (origen1, origen2, origen3).
1. Cree un nuevo inventario y asigne los tres orígenes al nuevo inventario.
   * Este stock debe asignarse al sitio web principal.
1. Cree un producto simple, P3, y asígnele todas las fuentes.
1. Añada las siguientes cantidades para los orígenes del producto simple y habilite los pedidos pendientes:
   * Origen predeterminado: 100
   * origen1 - 0
   * origen2 - 10
   * origen3 - 0
1. Añada el producto simple al carro de compras desde el front-end y continúe con el formulario de envío.
1. Seleccione &quot;source1&quot; como ubicación de envío.
1. Complete el orden y ejecute la siguiente consulta en la base de datos:

   ```sql
   SELECT * FROM inventory_reservation WHERE sku = 'P3';
   ```

   Obtendrá el registro de pedido realizado en la tabla `inventory_reservation`. La cantidad es 10, lo que es correcto.
1. Facturar este pedido desde el servidor.
1. Ahora cree un abono para un solo producto. NO active la casilla de verificación *Volver a Stock*.
1. Ejecute la misma consulta desde el paso 8.

<u>Resultados esperados</u>:

Si no seleccionó *Volver a stock* durante la creación de la nota de abono, la tabla `inventory_reservation` no tendrá un registro correspondiente a la nota de abono.

<u>Resultados reales</u>:

Aunque no seleccionó *Volver a stock* durante la creación de la nota de abono, agrega un registro a la tabla `inventory_reservation` con el tipo de evento `creditmemo_created`. Además, el registro de nota de abono agregado en la tabla `inventory_reservation` tiene una cantidad de 10 aunque haya creado la nota de abono para una sola cantidad.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
