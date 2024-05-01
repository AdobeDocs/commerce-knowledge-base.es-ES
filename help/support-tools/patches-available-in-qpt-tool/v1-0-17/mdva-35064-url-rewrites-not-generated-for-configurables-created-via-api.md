---
title: "MDVA-35064: Las reescrituras de URL no se generan para los configurables creados mediante API"
description: El parche de MDVA-35064 soluciona el problema de que no se generan reescrituras de URL para "Todas las vistas de tiendas" para productos creados mediante API. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.
exl-id: 0898c5b3-d361-4bcb-af3a-7f76ac8a23e1
feature: REST, Categories, Configuration
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# MDVA-35064: Las reescrituras de URL no se generan para los configurables creados mediante API

El parche de MDVA-35064 soluciona el problema de que no se generan reescrituras de URL para &quot;Todas las vistas de tiendas&quot; para productos creados mediante API. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 está instalado. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.5-p1

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.3-2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando se crean productos configurables mediante API, no se generan las reescrituras de URL.

<u>Pasos a seguir</u>:

1. Crear un nuevo sitio web, tienda y vista de tienda.
1. Cree una nueva categoría.
1. Cree un nuevo producto y asígnelo a la categoría recién creada.
1. Asigne el producto al sitio web principal y al nuevo sitio web.
1. Compruebe la tabla de URL y asegúrese de que contiene entradas para el producto, categoría/producto para cada tienda en cada sitio web.
1. Elimine el producto para el segundo sitio web.

<u>Resultados esperados</u>:

La tabla URL contiene entradas para el producto, categoría o producto solo para las tiendas del primer sitio web.

<u>Resultados reales</u>:

La tabla URL contiene las reescrituras de URL de todas las tiendas de todos los sitios web.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
