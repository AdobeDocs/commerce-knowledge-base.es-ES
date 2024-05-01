---
title: "MDVA-34330: Pedidos no filtrados según la zona horaria de administración"
description: El parche MDVA-34330 resuelve el problema en el que los pedidos no se filtran según la zona horaria de administración. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24. El ID del parche es MDVA-34330. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.
exl-id: cb369ee3-60b0-4317-a448-0c4ed64f2816
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# MDVA-34330: Pedidos no filtrados según la zona horaria de administración

El parche MDVA-34330 resuelve el problema en el que los pedidos no se filtran según la zona horaria de administración. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 está instalado. El ID del parche es MDVA-34330. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en la infraestructura en la nube 2.4.1

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce (todos los tipos de implementación) 2.3.1 - 2.4.2-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Pedidos no filtrados según la zona horaria de administración.

<u>Pasos a seguir</u>:

1. Ir a **Tiendas** > Configuración > **Configuración** > **General** y configure el **Timezone** hasta *Hora estándar del Este (América/Nueva_York)*
1. Realice un nuevo pedido después de las 00:00 UTC
1. Ir a **Ventas** > **Pedidos** y filtrar por fecha de hoy


<u>Resultados esperados</u>:

El pedido realizado hoy después de las 00:00 UTC es visible en los resultados filtrados.

<u>Resultados reales</u>:

Falta el orden en los resultados filtrados.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos en función del tipo de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sección.
