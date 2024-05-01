---
title: "MDVA-34867: Los valores del conjunto de campos de condición para la actualización programada no se han guardado"
description: El parche MDVA-34867 soluciona el problema de que el valor de la condición en la nueva actualización de programación no se guarda al editar una regla de precios de catálogo. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17. Tenga en cuenta que el problema se corrigió en la versión 2.4.3 de Adobe Commerce.
exl-id: bf514ccc-bebd-4ed2-868f-28b02b1e253e
feature: Catalog Management, Categories
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# MDVA-34867: Los valores del conjunto de campos de condición para la actualización programada no se han guardado

El parche MDVA-34867 soluciona el problema de que el valor de la condición en la nueva actualización de programación no se guarda al editar una regla de precios de catálogo. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 está instalado. Tenga en cuenta que el problema se corrigió en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.4.0-p1

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.0 - 2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El valor de la condición en la nueva actualización de programación no se guarda al editar una regla de precios de catálogo.

<u>Pasos a seguir</u>:

1. Inicie sesión en Admin.
1. Crear un **Regla de catálogo** con **Condición** = &quot;*La categoría es 1*&quot;.
1. Programar una actualización con una fecha de inicio futura (por ejemplo, mañana) y establecer **Condición** = &quot;*Categoría es 2, 3*&quot; y guarde la actualización.
1. Haga clic en **Ver/Editar** para la actualización creada anteriormente y compruebe los campos de condición.

<u>Resultados esperados</u>:

El **Reglas de catálogo**  **Condición** = &quot;*Categoría es 2, 3*&quot;, como se esperaba.

<u>Resultados reales</u>:

El **Reglas de catálogo**  **Condición** = &quot;*La categoría es 1*&quot;, lo que significa que la actualización no se ha guardado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
