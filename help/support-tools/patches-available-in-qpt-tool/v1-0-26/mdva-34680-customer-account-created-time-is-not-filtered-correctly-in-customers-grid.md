---
title: "MDVA-34680: La cuenta del cliente no se filtra correctamente en la cuadrícula de los clientes"
description: El parche MDVA-34680 corrige el problema cuando la cuenta del cliente creada después de las 00:00 UTC no se filtra correctamente en la cuadrícula de los clientes. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26. El ID del parche es MDVA-34680. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.
exl-id: 2e506d7a-8cde-41eb-84b2-1a5ff8015428
feature: Customer Service
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-34680: La cuenta del cliente no se filtra correctamente en la cuadrícula de los clientes

El parche MDVA-34680 corrige el problema cuando la cuenta del cliente creada después de las 00:00 UTC no se filtra correctamente en la cuadrícula de los clientes. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 está instalado. El ID del parche es MDVA-34680. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en la infraestructura en la nube 2.4.1 y 2.4.2

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.6-2.3.7 y 2.4.1-2.4.2-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando se crea una cuenta de cliente después de las 00:00 UTC y se intenta filtrar las cuentas por esa fecha, no se devuelve este cliente.

<u>Pasos a seguir</u>:

1. Ir a **Tiendas** > **Configuración** > **General** y establezca la Zona horaria en Estándar del Este [Estados Unidos/Nueva York].
1. Cree una nueva cuenta de cliente después de las 00:00 UTC.
1. Ir a **Clientes** > **Todos los clientes** y filtre las cuentas por fecha de hoy.

<u>Resultados esperados</u>:

Los filtros de cuenta de cliente muestran la nueva cuenta creada hoy después de las 00:00 UTC.

<u>Resultados reales</u>:

Los filtros de cuenta de cliente no muestran la nueva cuenta creada hoy.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sección.
