---
title: "MDVA-34943: El pedido rápido no puede añadir más de 2 productos al carro de compras"
description: El parche MDVA-34943 resuelve el problema en el que un pedido rápido no puede añadir dos o más productos al carro de compras. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17. Tenga en cuenta que el problema se corrigió en la versión 2.4.2 de Adobe Commerce.
exl-id: fcff6a78-fe00-4352-b0bc-149bd411d999
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---

# MDVA-34943: El pedido rápido no puede añadir más de 2 productos al carro de compras

El parche MDVA-34943 resuelve el problema en el que un pedido rápido no puede añadir dos o más productos al carro de compras. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 está instalado. Tenga en cuenta que el problema se corrigió en la versión 2.4.2 de Adobe Commerce.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.4.0-p1

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.0 - 2.4.1-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios no pueden agregar dos o más productos al carro de compras en orden rápido.

<u>Requisitos previos</u>:

Adobe Commerce con productos simples.

<u>Pasos a seguir</u>:

1. Ir a **Pedido rápido** en la Tienda (sin haber iniciado sesión).
1. Introduzca un SKU válido, haga clic en el producto que aparece en el campo Autocompletar y defina **Cantidad** = *1*.
1. Introduzca el mismo SKU válido, pero cambie el primer carácter a mayúscula (cambie las mayúsculas a minúsculas o cambie las minúsculas a mayúsculas) y haga clic en el producto que aparece en el campo de autocompletar y establezca **Cantidad** = *1*.
1. Introduzca una `random_sting_value` para **SKU** y establezca **Cantidad** = *1*.
1. Establecer **SKU** = *123123123* y establezca **Cantidad** = *1*.
1. Elimine todo excepto la primera entrada agregada al **Pedido rápido** página.
1. Introduzca el primer SKU (similar al paso 2 anterior) en la **Introducir varios SKU** y haga clic en **Añadir a lista**.
1. Esto da como resultado una cantidad de 2 para el primer SKU y una línea para un `random_sting_value`.
1. Para probar más, actualice la página.
1. Esto no da como resultado SKU para pedidos rápidos, como se esperaba.
1. Introduzca una `random_sting_value2` en el **Introducir varios SKU** y haga clic en **Añadir a lista**.
1. Esto da como resultado dos SKU válidas de antes y una `random_sting_value2`.

<u>Resultados esperados</u>:

Se pueden añadir dos o más productos al carro de compras, según lo esperado.

<u>Resultados reales</u>:

Cuando se lleva a **Carrito** página, el primer producto añadido aparece con normalidad, pero para el segundo producto y los productos subsiguientes añadidos al carro de compras, un &quot;*1 producto requiere atención* Aparece el mensaje de error &quot;. El segundo o cualquier producto adicional se enumerará en la **El producto requiere atención** de la sección **Carrito** página.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
