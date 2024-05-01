---
title: "MDVA-30945: un error grave durante las operaciones de añadir y actualizar el carro de compras"
description: El parche de MDVA-30945 soluciona el problema en el que se produce un error grave *Call to a member function getValue() on null en module-configurable-product CartItemProcessor.php* al actualizar los carros de compras. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. El problema se solucionó en Adobe Commerce 2.4.2.
exl-id: 0950e91b-900b-421d-91e7-abbfca4f30be
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-30945: error grave durante las operaciones de añadir y actualizar el carro de compras

El parche MDVA-30945 soluciona el problema en el que se produce un error grave *Llamada a una función miembro getValue() en null en module-configurable-product CartItemProcessor.php* al actualizar carros de compras. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalado. El problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Un error PHP fatal después de que los productos en el carrito se actualicen en el Administrador.

<u>Pasos a seguir</u>:

1. En el Administrador de Commerce, cree un producto configurable sin opciones.
1. Añádalo al carro de compras en la tienda.
1. Vuelva a Administración, añada opciones configurables al producto y guarde los cambios.
1. Actualice la página del carro de compras en la tienda.

<u>Resultados esperados</u>:

En la página del carro de compras, se muestra el siguiente mensaje de validación: *Algunos de los productos siguientes no tienen todas las opciones requeridas*.

<u>Resultados reales</u>:

La página del carro está en blanco. En el PHP `error.log`, se registra el siguiente error: *Excepción no detectada &quot;Error&quot; con el mensaje &quot;Llamada a una función miembro getValue() en null&quot; en vendor/magento/module-configurable-product/Model/Quote/Item/CartItemProcessor.php:76*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
