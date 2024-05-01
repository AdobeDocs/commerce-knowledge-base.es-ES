---
title: "MDVA-34012 patch: la casilla de verificación de atributos cambia por error"
description: El parche MDVA-34012 resuelve el problema en el que la casilla de verificación de un atributo se cambia después de una actualización de programación por error.
exl-id: 1a8f1bea-9b6a-4984-b9f0-b2b9ceb6688f
feature: Attributes
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# Parche MDVA-34012: cambios en la casilla de verificación de atributos por error

El parche MDVA-34012 resuelve el problema en el que la casilla de verificación de un atributo se cambia después de una actualización de programación por error.

Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.17 está instalado. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:** Adobe Commerce en infraestructura en la nube 2.3.5-p2

**Compatible con las versiones de Adobe Commerce:** Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.1 - 2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir</u>:

1. Inicie sesión en Admin y vaya a **Catálogo > Productos**.
1. Edite cualquier producto simple.
1. Cambie la vista de tienda a una vista de tienda específica.
1. Guarde el producto con **Usar valor predeterminado** casilla de verificación seleccionada para un atributo (Ejemplo: **Activar producto** atributo).
1. Haga clic en **Programar nueva actualización** para programar algunos cambios (Ejemplo: **Precio** o **Precio especial** para una vista de tienda específica).
1. Espere hasta que se completen los cambios.
1. Compruebe el producto. Debe tener su casilla de verificación sin seleccionar y debe tener un valor de atributo de almacén específico.

<u>Resultados esperados</u>:

La casilla de verificación del atributo debe ser la misma y no se cambiará después de la actualización de la programación, según lo esperado.

<u>Resultados reales</u>:

La casilla de verificación del atributo se cambia después de actualizar la programación.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos, según el producto de Adobe Commerce:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en la herramienta QPT, consulte la [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
