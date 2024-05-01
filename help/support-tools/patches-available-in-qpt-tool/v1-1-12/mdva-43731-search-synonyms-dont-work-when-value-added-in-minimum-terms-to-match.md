---
title: "MDVA-43731: Los sinónimos de búsqueda no funcionan cuando se agrega un valor en 'Términos mínimos de coincidencia'"
description: El parche MDVA-43731 corrige el problema en el que los sinónimos de búsqueda dejan de funcionar cuando se agrega un valor en "Términos mínimos de coincidencia". Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. El ID del parche es MDVA-43731. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: b795989c-d10b-443e-aebe-f3859930396a
feature: Cache, Marketing Tools, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 0%

---

# MDVA-43731: Los sinónimos de búsqueda no funcionan cuando se agrega un valor en &quot;Términos mínimos de coincidencia&quot;

El parche MDVA-43731 corrige el problema en el que los sinónimos de búsqueda dejan de funcionar cuando se agrega un valor en &quot;Términos mínimos de coincidencia&quot;. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 está instalado. El ID del parche es MDVA-43731. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los sinónimos de búsqueda dejan de funcionar cuando se agrega un valor en &quot;Términos mínimos que deben coincidir&quot;.

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce con datos de ejemplo.
1. Configure Elasticsearch7 como motor de búsqueda.
1. Busca la palabra &quot;Chaqueta&quot;. Se mostrará una lista de productos.
1. Añadir el parámetro [4&lt;60 %] in **Configuración** > **Catálogo** > **Búsqueda en catálogo** > **Términos mínimos que deben cumplirse**.
1. Borre la caché de configuración y vuelva a indexar.
1. De nuevo busque la palabra &quot;Chaqueta&quot; y observe que se muestra una lista de productos.
1. Ir a **Marketing** > **SEO y búsqueda** > **Buscar sinónimos**.
1. Cree Sinónimos de búsqueda añadiendo los siguientes sinónimos: jacket, bagtecs, express plus.
1. Realice una reindexación.
1. Realice una búsqueda de productos utilizando cualquiera de los sinónimos. Por ejemplo, chaqueta.

<u>Resultados esperados</u>:

Obtendrá la misma lista de productos que antes en los resultados de búsqueda.

<u>Resultados reales</u>:

No se muestra ningún producto en los resultados de búsqueda.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
