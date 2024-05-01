---
title: "MDVA-27456: Los usuarios reciben un error al cargar Swagger"
description: El parche MDVA-27456 corrige el problema en el que los usuarios reciben un error al intentar cargar Swagger. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6. El ID del parche es MDVA-27456. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.3.7.
exl-id: e331595f-a94b-4070-803a-60f559735b29
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# MDVA-27456: Los usuarios reciben un error al cargar Swagger

El parche MDVA-27456 corrige el problema en el que los usuarios reciben un error al intentar cargar Swagger. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6 está instalado. El ID del parche es MDVA-27456. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.3.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.5-p1

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.5 - 2.3.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios reciben un error al cargar Swagger.

<u>Pasos a seguir</u>:

Ir a `../swagger.`

<u>Resultados esperados</u>:

Swagger se carga sin ningún error.

<u>Resultados reales</u>:

Los usuarios reciben el siguiente error: *Error al cargar la definición de API*. El registro de errores contiene:

*report.CRITICAL: ID del informe: webapi-5ea9c6da19cb1; mensaje: el tipo de parámetro &quot;\DateTime&quot; no es válido. Compruebe el parámetro e inténtelo de nuevo.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
