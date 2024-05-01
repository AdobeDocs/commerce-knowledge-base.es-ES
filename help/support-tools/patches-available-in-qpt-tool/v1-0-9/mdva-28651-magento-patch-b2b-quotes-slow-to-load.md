---
title: "MDVA-28651: B2B: las comillas tardan en cargarse"
description: El parche MDVA-28651 resuelve el problema en el que se producen varios problemas de rendimiento con la carga de presupuestos. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.9. Tenga en cuenta que el problema estaba programado para solucionarse en la versión 2.4.2 de Adobe Commerce.
exl-id: 2d0bfbba-cdf3-4f9e-a900-ce42909fac8e
feature: B2B, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-28651: B2B: las cotizaciones tardan en cargarse

El parche MDVA-28651 resuelve el problema en el que se producen varios problemas de rendimiento con la carga de presupuestos. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.9 está instalado. Tenga en cuenta que el problema estaba programado para solucionarse en la versión 2.4.2 de Adobe Commerce.

## Productos y versiones afectados

* El parche se ha diseñado para Adobe Commerce en la infraestructura en la nube 2.3.4.
* El parche también es compatible con las siguientes versiones de Adobe Commerce: Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.0-2.3.5-p1, 2.4.0 y 2.4.1.

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Problemas de rendimiento en la página de lista de presupuesto de cliente:

* carga doble de la lista de cotización: primero con toda la página, segundo por la solicitud de Ajax.
* un bucle de carga de cada una de las comillas del complemento.
* carga doble de los elementos de oferta cuando el presupuesto se convirtió en la instantánea.

<u>Pasos a seguir</u>

1. Tiene más de 40 presupuestos asignados a un cliente.
1. Inicie sesión y explore **Mis comillas** página.

<u>Resultado real</u>

El tiempo de respuesta para cargar completamente el contenido del **Mis comillas** página (carga de la página + datos mostrados en la cuadrícula) es ~ 45 segundos.

<u>Resultado esperado</u>

El tiempo de respuesta para cargar completamente el contenido del **Mis comillas** debe ser inferior a 45 segundos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sección.
