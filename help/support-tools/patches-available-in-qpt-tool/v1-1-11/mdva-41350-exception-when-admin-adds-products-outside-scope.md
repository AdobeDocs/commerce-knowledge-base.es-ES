---
title: "MDVA-41350: Excepción cuando el administrador agrega productos fuera de su acceso"
description: El parche MDVA-41350 corrige el problema en el que se produce un error de excepción en lugar de una notificación de acceso limitado cuando un usuario administrador añade un producto en el pedido por SKU que está fuera de su acceso. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11. El ID del parche es MDVA-41350. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: 3a96d029-5350-4dd6-aad3-2f2cdd5e65ac
feature: Admin Workspace, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-41350: Excepción cuando el administrador agrega productos fuera de su acceso

El parche MDVA-41350 corrige el problema en el que se produce un error de excepción en lugar de una notificación de acceso limitado cuando un usuario administrador añade un producto en el pedido por SKU que está fuera de su acceso. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11. El ID del parche es MDVA-41350. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando un usuario administrador con acceso restringido añade un producto por SKU fuera de su acceso en el pedido, se produce una excepción en lugar de un mensaje que notifica al usuario su acceso limitado.

<u>Pasos a seguir</u>:

1. Inicie sesión en el administrador como un usuario con acceso solo a un sitio web específico.
1. Vaya a **Ventas** > **Pedidos** y haga clic en **Crear nuevo pedido**.
1. Seleccione una vista de cliente y otra de tienda.
1. Haz clic en **Agregar productos por SKU**.
1. Busque un SKU que no esté asignado a ningún sitio web o que no esté asignado al sitio web al que tiene acceso.
1. Haga clic en **Agregar a pedido**.

<u>Resultados esperados</u>:

Se muestra un mensaje de error apropiado.

<u>Resultados reales</u>:

Se produce una excepción.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
