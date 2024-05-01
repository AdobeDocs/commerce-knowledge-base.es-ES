---
title: "MDVA-35982: No se pueden enviar algunos pedidos"
description: El parche MDVA-35982 corrige el error cuando el usuario administrador restringido a un sitio web específico no puede crear un envío para el pedido realizado en el mismo sitio web. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. El ID del parche es MDVA-35982. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.
exl-id: f41c6572-66bb-4697-93e3-da34b81829e2
feature: Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-35982: No se pueden enviar algunos pedidos

El parche MDVA-35982 corrige el error cuando el usuario administrador restringido a un sitio web específico no puede crear un envío para el pedido realizado en el mismo sitio web. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 está instalado. El ID del parche es MDVA-35982. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.5-p1

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El comerciante no puede enviar ciertas órdenes.

<u>Pasos a seguir</u>:

1. Seleccione cualquier sitio web de producto para el producto, excepto la tienda predeterminada. Consulte [Producto en sitios web](https://docs.magento.com/user-guide/catalog/settings-basic-websites.html) en nuestra guía del usuario para ver los pasos detallados.
1. Cree una función de usuario para el administrador con ámbitos de función personalizados, en la que el sitio web o la tienda predeterminados no estén seleccionados. Consulte [Definir una función](https://docs.magento.com/user-guide/system/permissions-user-roles.html#define-a-role) en nuestra guía del usuario para ver los pasos detallados.
1. Abra el producto en modo de edición y establezca un Precio de grupo para este producto, en **Precios avanzados**. Consulte [Precio de grupo](https://docs.magento.com/user-guide/catalog/product-price-group.html) en nuestra guía del usuario para ver los pasos detallados.
1. Cree un pedido con este producto.
1. Inicie sesión en Admin con este rol de usuario y cree un envío. Consulte [Creación de Envíos](https://docs.magento.com/user-guide/sales/shipments-create.html) en nuestra guía del usuario para ver los pasos detallados.

<u>Resultados esperados</u>:

Se crea el envío.

<u>Resultados reales</u>:

Se muestra el siguiente error:

`"0":"Notice: Undefined offset: XX in \/vendor\/magento\/module-catalog\/Model\/Product\/Attribute\/Backend\/GroupPrice\/AbstractGroupPrice.php on line 290"`

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
