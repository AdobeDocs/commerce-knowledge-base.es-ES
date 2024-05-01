---
title: "MDVA-41061: El estado de las existencias se restablece como vendible cuando el producto se guarda desde el administrador"
description: El parche MDVA-41061 corrige el problema en el que el estado de las existencias se restablece como comercializable cuando el producto se guarda desde el administrador. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5. El ID del parche es MDVA-41061. La última versión del parche está disponible en QPT 1.1.15 con ID de parche MDVA-41061-V3. Tenga en cuenta que el problema se corrige en Adobe Commerce 2.4.4.
exl-id: fd71d3e5-685f-4987-b7e7-bfd86810d865
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-41061: El estado de las existencias se restablece como vendible cuando el producto se guarda desde el administrador

El parche MDVA-41061 corrige el problema en el que el estado de las existencias se restablece como comercializable cuando el producto se guarda desde el administrador. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5 está instalado. El ID del parche es MDVA-41061. La última versión del parche está disponible en QPT 1.1.15 con ID de parche MDVA-41061-V3. Tenga en cuenta que el problema se corrige en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.2-p2, 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El estado de stock se restablece como comercializable cuando el producto se guarda desde el administrador.

<u>Requisitos previos</u>:

Módulos de inventario instalados.

<u>Pasos a seguir</u>:

1. Cree un producto simple con Cantidad = 1.
1. Realice un pedido utilizando el producto creado en el paso 1.
1. Ejecutar cron: asegúrese de `inventory.reservations.updateSalabilityStatus` se ejecuta la cola y el estado de las existencias del producto se ha cambiado a cero en la `cataloginventory_stock_status` tabla.
1. Compruebe el producto en el front-end. Debe marcarse como. **Sin existencias**.
1. Guarde el producto en Admin sin ningún cambio.

<u>Resultados esperados</u>:

* El estado de las existencias no debe actualizarse.
* El producto debe ser **Sin existencias** en la interfaz.

<u>Resultados reales</u>:

* El producto simple está marcado como **En stock** en la interfaz.
* Los usuarios obtienen *La cantidad solicitada no está disponible* al intentar añadirlo al carro de compras.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
