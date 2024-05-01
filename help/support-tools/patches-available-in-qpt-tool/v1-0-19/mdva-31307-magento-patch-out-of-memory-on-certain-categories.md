---
title: "MDVA-31307: Memoria insuficiente en determinadas categorías"
description: El parche MDVA-31307 soluciona el problema de que "Magento\_Csp/Modelo/BlockCache" consume mucha memoria y genera enormes cadenas en caché, lo que causa problemas en ciertas páginas con muchos scripts y estilos en la lista blanca de forma dinámica. El parche proporcionado optimiza este proceso. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. El ID del parche es MDVA-31307. Tenga en cuenta que el problema se corrige en Adobe Commerce 2.4.2.
exl-id: 15d82f5b-bd43-4a0a-b756-d109dac6d2cd
feature: Cache, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-31307: Memoria insuficiente en determinadas categorías

El parche MDVA-31307 soluciona el problema donde `Magento\_Csp/Model/BlockCache` consume mucha memoria y genera enormes cadenas en caché, lo que causa problemas para ciertas páginas con muchos scripts y estilos en la lista blanca de forma dinámica. El parche proporcionado optimiza este proceso. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 está instalado. El ID del parche es MDVA-31307. Tenga en cuenta que el problema se corrige en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:** Adobe Commerce en infraestructura en la nube 2.4.0

**Compatible con las versiones de Adobe Commerce:** Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Soluciona el problema donde hay *Memoria insuficiente* errores en ciertas categorías debido a problemas con la lista blanca de CSP dinámicos para bloques en caché.

<u>Pasos a seguir:</u>

1. Generar accesorios de perfil pequeños (`bin/magento setup:performance:generate-fixtures`).
1. Abra todas las páginas de categorías en pestañas diferentes.

<u>Resultado real:</u>

*[fecha y hora] Error grave de PHP: tamaño de memoria permitido de 1073741824 bytes agotados (se intentó asignar 90112 bytes) en Desconocido en la línea 0
[fecha y hora] Error grave de PHP: tamaño de memoria permitido de 1073741824 bytes agotado (se intentó asignar 33554440 bytes) en /app/`<project-id>`/vendor/magento/module-csp/Model/Collector/DynamicCollector.php en la línea 31*

<u>Resultado esperado:</u>

Todas las páginas se han abierto correctamente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sección.
