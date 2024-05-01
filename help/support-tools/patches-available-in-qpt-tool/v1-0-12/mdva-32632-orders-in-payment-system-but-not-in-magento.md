---
title: "MDVA-32632: Pedidos en el sistema de pago pero no en Adobe Commerce"
description: El MDVA-32632 soluciona el problema de los pedidos en un sistema de pago, pero no en Adobe Commerce. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.3.5.
exl-id: f9b2fee4-9905-47cb-a71a-121426e93beb
feature: Orders, Payments, System
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# MDVA-32632: Pedidos en sistema de pago pero no en Adobe Commerce

El MDVA-32632 soluciona el problema de los pedidos en un sistema de pago, pero no en Adobe Commerce. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 está instalado. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.3.5.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.2-p2

**El parche también es compatible con la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.2 - 2.3.4-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El pago se procesa en un sistema de pago, pero el pedido no se crea en Adobe Commerce.

<u>Pasos a seguir</u>:

1. Realice el pedido utilizando un método de pago en línea.
1. Compruebe el pedido en el Administrador de Commerce.

<u>Resultados esperados</u>:

Los pedidos completados ahora aparecen en el sistema de pago y en Adobe Commerce.

<u>Resultados reales</u>:

El sistema de pago ha procesado correctamente los pedidos, pero no en Adobe Commerce.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
