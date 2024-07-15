---
title: "MDVA-44533: descuento aplicado incorrectamente al producto secundario empaquetado"
description: El parche MDVA-44533 corrige el problema en el que un descuento se aplica incorrectamente a un producto secundario empaquetado. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15. El ID del parche es MDVA-44533. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: 84302ed4-d850-45e4-8b5b-44495f9df820
feature: Orders, Personalization, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-44533: descuento aplicado incorrectamente al producto secundario empaquetado

El parche MDVA-44533 corrige el problema en el que un descuento se aplica incorrectamente a un producto secundario empaquetado. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15. El ID del parche es MDVA-44533. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.1 - 2.4.3-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El descuento se aplica incorrectamente a un producto secundario empaquetado.

<u>Pasos a seguir</u>:

1. Crea un producto sencillo con un precio de 50$.
1. Cree un producto agrupado y asigne el producto simple como la única opción para el producto agrupado.
1. Crear una regla de precio de carro de compras con:

   * Condición: si la cantidad total es mayor que 130 $
   * Acción: se aplica un descuento de importe fijo de 10$

1. Vaya a la tienda y añada el producto del paquete al carro con la cantidad = 1.
1. Vaya al carro y compruebe que el coste total del producto del paquete es de 50 $ y que no se aplica el descuento.
1. Cambie la cantidad a 2 y actualice el carro de compras. El coste total del producto agrupado ahora debe ser de 100 $.

<u>Resultados esperados</u>:

El descuento no se aplica porque el subtotal es 100\$, que es inferior a 130\$ en la condición de regla.

<u>Resultados reales</u>:

Se aplica el descuento.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
