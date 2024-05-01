---
title: "parche del Magento MDVA-23764: error al cargar bloques dinámicos"
description: El parche del Magento MDVA-23764 corrige el error en
exl-id: b884ade6-f88d-4c79-8e84-5a59252abb75
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Parche del Magento MDVA-23764: error al cargar bloques dinámicos

El parche del Magento MDVA-23764 corrige el error en

```php
JsFooterPlugin.php
```

que afecta a la visualización de bloques dinámicos. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 está instalado. Tenga en cuenta que el problema se solucionó en el Magento 2.3.5.

## Productos y versiones afectados

**El parche se crea para la versión de Magento:** Magento Commerce Cloud 2.3.3.

**Compatible con versiones de Magento:** Magento Commerce y Magento Commerce Cloud 2.3.2 - 2.3.4-p2.

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir:</u>

Intente cargar una dirección URL similar a la siguiente: https://\[dominio de magento\]/banner/ajax/load/.

<u>Resultado real:</u>

Se genera un error similar al siguiente: *TypeError no capturado: strpos() espera que el parámetro 1 sea una cadena, nulo se da en...(línea de código)* .

<u>Resultado esperado:</u>

La URL se carga sin errores.

## Aplicar el parche

Para obtener instrucciones sobre cómo aplicar un parche QPT, utilice los siguientes enlaces según el producto de su Magento:

* Magento Commerce: DevDocs [Aplicación de parches mediante la herramienta Parches de calidad](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) .
* Magento Commerce Cloud: DevDocs [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) .

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) .
* [Comprobar si el parche está disponible para el problema del Magento mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) .

Para obtener más información sobre otros parches disponibles en la herramienta QPT, consulte la [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
