---
title: "MDVA-36021: Los usuarios reciben un mensaje de error al abrir los detalles del pedido"
description: El parche MDVA-36021 soluciona el problema en el que los usuarios reciben el mensaje de error *Call to a member function getId()* al intentar abrir los detalles del pedido. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1. El ID del parche es MDVA-36021. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: 73b1f3c6-5dc4-48e4-8f3f-681be84f7638
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-36021: Los usuarios reciben un mensaje de error al abrir los detalles del pedido

El parche MDVA-36021 resuelve el problema en el que los usuarios obtienen *Llamada a una función de miembro getId()* mensaje de error al intentar abrir los detalles del pedido. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 está instalado. El ID del parche es MDVA-36021. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce en infraestructura en la nube 2.4.1, 2.4.2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.2-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando los usuarios intentan abrir los detalles del pedido, aparece el siguiente mensaje de error en la página de detalles del pedido en el Administrador: *report.CRITICAL: Error: Llamada a una función miembro getId() en una matriz en /magento2ce/app/code/Magento/Sales/view/adminhtml/templates/order/totals/tax.phtml:62*.

<u>Requisitos previos</u>:

El sistema debe tener configuraciones de impuestos y pedidos con tasas de impuestos específicas.

<u>Pasos a seguir</u>:

1. Inicie sesión en el administrador de Commerce.
1. Ir a **Ventas** > **Pedidos** > **Abrir pedido**.

<u>Resultados esperados</u>:

El pedido se abre sin ningún error.

<u>Resultados reales</u>:

Aparece un mensaje de error similar al siguiente: *report.CRITICAL: Error: Llamada a una función miembro getId() en una matriz en /magento2ce/app/code/Magento/Sales/view/adminhtml/templates/order/totals/tax.phtml:62*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
