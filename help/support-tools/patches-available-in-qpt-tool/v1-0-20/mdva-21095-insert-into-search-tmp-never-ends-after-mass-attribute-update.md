---
title: 'MDVA-21095: INSERT INTO "search_tmp..." no termina nunca después de la actualización masiva de atributos'
description: El parche MDVA-21095 soluciona el problema cuando una consulta "INSERT INTO" "search\_tmp..." no termina nunca después de una actualización masiva de atributos. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. El ID del parche es MDVA-21095. Tenga en cuenta que no hay ningún plan actual para solucionar este problema en versiones futuras.
exl-id: fd599473-b49a-4f9c-a13f-612d05e43f09
feature: Attributes, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# MDVA-21095: INSERT INTO &quot;search_tmp...&quot; no termina nunca después de la actualización masiva de atributos

El parche MDVA-21095 corrige el problema cuando se realiza una consulta `INSERT INTO` &quot;search\_tmp...&quot; nunca termina después de una actualización masiva de atributos. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 está instalado. El ID del parche es MDVA-21095. Tenga en cuenta que no hay ningún plan actual para solucionar este problema en versiones futuras.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.2

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.3.4-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

`INSERT INTO` &quot;search\_tmp...&quot; nunca termina después de una actualización masiva de atributos.

<u>Paso para reproducir</u>:

Realice una actualización masiva de valores de atributos con ~30,000 elementos.

<u>Resultados esperados</u>:

El proceso de reindexación se completa normalmente, según lo esperado.

<u>Resultados reales</u>:

El proceso de reindexación se completa, pero muchas consultas `INSERT INTO` &quot;search\_tmp...&quot; hasta que el servidor alcance el `pm.max_children` El valor de parámetro y PHP-fpm mueren, y estos se repiten constantemente incluso después de reiniciar MySQL y matar el proceso.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
