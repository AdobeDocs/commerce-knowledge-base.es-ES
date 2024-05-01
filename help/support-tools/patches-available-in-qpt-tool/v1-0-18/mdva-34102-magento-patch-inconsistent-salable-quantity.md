---
title: "MDVA-34102: cantidad vendible incoherente"
description: El parche de MDVA-34102 resuelve el problema en el que la cantidad de existencias predeterminadas es cero para los productos desactivados en las páginas Cuadrícula de productos y Editar producto en el Administrador. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18. El ID del parche es MDVA-34102. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.3 de Adobe Commerce.
exl-id: cb1d4689-c122-4afd-8597-b2627027aaf3
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-34102: cantidad vendible inconsistente

El parche de MDVA-34102 resuelve el problema en el que la cantidad de existencias predeterminadas es cero para los productos desactivados en las páginas Cuadrícula de productos y Editar producto en el Administrador. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 está instalado. El ID del parche es MDVA-34102. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.5-p2

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.0-2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir</u>:

1. Configurar dos sitios web con tiendas y vistas de tiendas.
1. Crear un origen y un stock adicionales.
1. Añada un producto simple:
   * Establecer **Activar producto** = *No*.
   * Asignar dos fuentes con **Estado del elemento de origen** = *En stock* con una cantidad mayor que cero (Ejemplo: **existencias por defecto** = *123* y **acciones del Reino Unido** = *123*).
1. Guarde el producto.
1. Compruebe la **Cantidad vendible del producto** pestaña.

<u>Resultados esperados</u>:

Tanto las acciones por defecto como las acciones del Reino Unido = *123.*

La cantidad de stock predeterminado se muestra correctamente para los productos desactivados en las páginas Cuadrícula de productos y Editar producto en el Administrador.

<u>Resultados reales</u>:

El stock predeterminado = *0* y las acciones del Reino Unido = *123.*

La cantidad de existencias predeterminada es cero para los productos desactivados en las páginas Cuadrícula de productos y Editar producto en el Administrador.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en la herramienta QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
