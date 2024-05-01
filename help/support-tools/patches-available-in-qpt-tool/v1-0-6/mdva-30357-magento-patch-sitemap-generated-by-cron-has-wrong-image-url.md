---
title: "MDVA-30357: el mapa del sitio generado por cron tiene una URL de imagen incorrecta"
description: El parche MDVA-30357 corrige el problema con la URL de imagen incorrecta que se crea mediante un mapa del sitio generado por Cron en el administrador de Commerce. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.
exl-id: c91f7ae0-0970-4918-9d1f-4ede6bfcb05f
feature: Marketing Tools
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 0%

---

# MDVA-30357: el mapa del sitio generado por cron tiene una URL de imagen incorrecta

El parche MDVA-30357 corrige el problema con la URL de imagen incorrecta que se crea mediante un mapa del sitio generado por Cron en el administrador de Commerce. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 está instalado. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

* Adobe Commerce (todos los métodos de implementación) 2.3.2 a 2.4.0

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los mapas del sitio generados por cron en Adobe Commerce contienen la ruta URL de imagen incorrecta.

<u>Pasos a seguir</u>:

1. En el Administrador de Commerce, cree un nuevo sitio web, tienda o vista de tienda.
1. Añada al menos un producto a cada tienda y añada al menos una imagen a cada producto.
1. Activar **Generación De Mapa Del Sitio Por Programación** in **Administrador** > **Tiendas** > **Configuración** > **CATÁLOGO** > **Mapa del sitio XML** > **Configuración de generación**.
1. Genere un mapa del sitio para cualquiera de las dos tiendas manualmente en **Administrador** > **Marketing** > **Mapa del sitio** con un nombre de mapa del sitio como &quot;*sitemap.xml*&quot;.
   * Cambie el nombre del archivo por otro similar a &quot;*manual\_sitemap.xml*&quot; o copie el contenido del archivo en cualquier editor de texto.
1. Generar el mismo mapa del sitio mediante trabajo cron `sitemap_generate`.
1. Comparar el mapa del sitio generado manualmente&quot;*manual\_sitemap.xml*&quot; y el mapa del sitio generado por cron &quot;*sitemap.xml*&quot;.

<u>Resultados esperados</u>:

La URL de ruta de imagen de mapa del sitio en caché es correcta.

<u>Resultados reales</u>:

El mapa del sitio generado por cron contiene la dirección URL de ruta de imagen incorrecta. Si intenta abrir la imagen desde &quot;*sitemap.xml*&quot;, mostrará un marcador de posición predeterminado. Las direcciones URL de mapas del sitio generadas manualmente no se ven afectadas por este problema.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.

Para obtener más información sobre los mapas del sitio, consulte estos artículos en nuestra documentación para desarrolladores:

* [Agregar robots de mapa del sitio y motores de búsqueda](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html)
* [Configurar y ejecutar cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html)
* [Asegure cron.php para ejecutar en un navegador](https://devdocs.magento.com/guides/v2.4/config-guide/secy/secy-cron.html)
