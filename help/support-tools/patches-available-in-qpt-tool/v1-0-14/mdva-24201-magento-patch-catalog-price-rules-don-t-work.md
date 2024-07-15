---
title: "MDVA-24201: Las reglas de precios de catálogo no funcionan"
description: El parche MDVA-24201 resuelve el problema de que las reglas de precios de catálogo activas en la base de datos no se aplican en el front-end.
exl-id: ae541c40-403a-46e9-a486-2a1e8991f05a
feature: Catalog Management, Categories, Marketing Tools, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-24201: Las reglas de precios de catálogo no funcionan

El parche MDVA-24201 resuelve el problema de que las reglas de precios de catálogo activas en la base de datos no se aplican en el front-end.

Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14. Tenga en cuenta que el problema se corrigió en la versión 2.3.5 de Adobe Commerce.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:** Adobe Commerce en la infraestructura en la nube 2.3.3

**Compatible con versiones de Adobe Commerce:** Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.0 - 2.3.4-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Requisito previo</u>:

Instale una nueva instancia de Magento con datos de ejemplo.

<u>Pasos a seguir</u>:

1. Inicie sesión en **Panel de administración** > **Marketing** > **Regla de precios de catálogo** > **Agregar nueva regla**, realice la siguiente configuración:
   1. Establezca el **nombre de regla**.
   1. Conjunto **Activo** = *No.*
   1. Establecer condiciones: **Categoría** = *4*. (Ejemplo: Bolsas)
   1. Establecer acciones:
      1. Establecer **Aplicar como**   **porcentaje del original**.
      1. Establecer **Importe de descuento** = *10*.
      1. Guarde y, a continuación, continúe editando.
   1. Haz clic en **Programar nueva actualización**:
      * Establezca el **nombre de regla**.
      * Definir **Activo** = *Sí*.
      * Guardar.
1. Vaya al servidor y ejecute:

   `php    bin/magento cron:run`

<u>Resultados esperados</u>:

Los precios de los productos de la categoría 4 &quot;Bolsas&quot; deben reducirse en un 10% del precio original, tal como se estableció por la regla de precios de catálogo, como se esperaba.

<u>Resultados reales</u>:

No se producen cambios de precio aunque la regla de precios de catálogo esté activa.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
