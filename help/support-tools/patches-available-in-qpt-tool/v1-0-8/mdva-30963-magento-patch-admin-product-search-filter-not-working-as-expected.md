---
title: "MDVA-30963: el filtro de búsqueda de productos de administración no funciona como se esperaba"
description: El parche MDVA-30963 resuelve el problema en el que el administrador de Commerce y el filtro de búsqueda de productos no funcionan según lo esperado. Los valores que se anulan en un ámbito de vista de almacén también se tienen en cuenta al filtrar en **Vista de todos los almacenes** ámbito de vista de almacén. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.
exl-id: bde2836e-8954-48e5-b411-08c951ec8620
feature: Admin Workspace, Products, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# MDVA-30963: el filtro de búsqueda de productos de administración no funciona como se esperaba

El parche MDVA-30963 resuelve el problema en el que el administrador de Commerce y el filtro de búsqueda de productos no funcionan según lo esperado. Los valores que se anulan en un ámbito de vista de tienda también se tienen en cuenta al filtrar **Vista de todas las tiendas** ámbito de vista de tienda. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 está instalado. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce en infraestructura en la nube 2.4.0

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.2 - 2.4.1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir</u>:

1. Establecer **Tiendas** > **Configuración** > **Catálogo** > **Catálogo** > **Precio** > **Precios de catálogo** = *Sitio web*.
1. Cree dos sitios web con dos monedas diferentes (por ejemplo, el sitio web predeterminado es una tienda de India \[₹ de rupia\] y el segundo es la tienda de EE. UU. \[dólar $\]).
1. Configure lo siguiente **Moneda base**, **Divisa para mostrar predeterminada**, y **Divisas permitidas**:
   * **Configuración predeterminada** = *Dólar estadounidense (predeterminado)*
   * **Sitio web principal** = *Rupia india*
   * **WebsiteUS** = **Usar valor predeterminado** = *Dólar estadounidense*
1. Establecer **Tiendas** > **Tipos de cambio** = *1:1*.
1. Cree un producto simple de prueba asignado a ambos sitios web con los siguientes precios:
   * **Precio predeterminado** = **Precio del sitio web** = *123 USD*
   * **Precio del sitio web principal** = *321 rupia*
1. Cree un usuario subAdmin que solo tenga acceso a la tienda de EE. UU.
1. Vaya a la tienda de EE. UU. y coloque un producto en el carro de compras (Ejemplo: *Precio de 123 USD*).
1. Inicie sesión en Admin con el subAdmin recién creado (Ejemplo: *Administrador solo de EE. UU.*).
1. Ir a **Informes** > **Productos en el carro**.

<u>Resultados esperados</u>:

Al filtrar dentro de **Vista de todas las tiendas** ámbito de vista del almacén, el filtrado de productos debe obtener el valor establecido en ese ámbito en particular.

<u>Resultados reales</u>:

Los valores anulados en un ámbito de vista de almacén también se tienen en cuenta al filtrar en el ámbito de vista de almacén &quot;Todas las vistas de almacén&quot;.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
