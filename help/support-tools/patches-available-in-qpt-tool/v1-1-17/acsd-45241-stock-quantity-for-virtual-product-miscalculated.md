---
title: "ACSD-45241: La cantidad de stock del producto virtual no se ha calculado correctamente"
description: El parche ACSD-45241 corrige el problema en el que la cantidad de existencias del producto virtual se calcula de forma incorrecta después de crear un abono. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17. El ID del parche es ACSD-45241. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.4.
exl-id: 4be97da9-d399-419a-816e-cf65f15cc3be
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# ACSD-45241: la cantidad de existencias del producto virtual se ha calculado incorrectamente

El parche ACSD-45241 corrige el problema en el que la cantidad de existencias del producto virtual se calcula de forma incorrecta después de crear un abono. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 está instalado. El ID del parche es ACSD-45241. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.5 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La cantidad de stock de un producto virtual se calcula incorrectamente después de crear una nota de abono.

<u>Pasos a seguir</u>:

1. Cree un producto configurable con un producto virtual como producto secundario en el administrador de Commerce.
1. Asegúrese de que ambos productos creados en el paso uno estén en stock.
1. Marque la cantidad del producto virtual creado en el paso uno como 100 y mantenga también la cantidad vendible como 100.
1. Añadir el producto al carro de compras.
1. Realice un pedido con el producto virtual creado en el paso uno.
1. Mantenga el estado del pedido como Pendiente. No es necesario procesar el pago.
1. `order_created` registro creado en `inventory_reservation`. La cantidad de producto virtual muestra 100 con una cantidad vendible de 99.
1. Abra la solicitud y vaya a **Factura** > **Enviar factura**.
1. `invoice_created` registro creado en `inventory_reservation`. La cantidad de producto virtual es ahora 99, y la cantidad vendible también es 99.
1. Crear un abono sin seleccionar **Volver a stock**.

<u>Resultados esperados</u>:

No se crea ningún registro nuevo en `inventory_reservation`y la cantidad de stock del producto virtual no cambia.

<u>Resultados reales</u>:

A `creditmemo_created` el registro se crea en `inventory_reservation`, y la cantidad de stock de producto virtual se ajusta a 98 con la cantidad vendible como 99.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
