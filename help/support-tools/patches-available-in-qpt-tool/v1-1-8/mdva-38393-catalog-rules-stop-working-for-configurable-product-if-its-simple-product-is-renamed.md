---
title: "MDVA-38393: Las reglas de catálogo dejan de funcionar para productos configurables si se cambia el nombre de su producto simple"
description: El parche de MDVA-38393 corrige el problema de que las reglas de catálogo dejan de funcionar para un producto configurable si se cambia el nombre de su producto simple. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8. El ID del parche es MDVA-38393. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: a20856c4-8aff-427b-a404-7afe706be06f
feature: Catalog Management, Categories, Configuration, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-38393: Las reglas de catálogo dejan de funcionar para productos configurables si se cambia el nombre de su producto simple

El parche de MDVA-38393 corrige el problema de que las reglas de catálogo dejan de funcionar para un producto configurable si se cambia el nombre de su producto simple. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 está instalado. El ID del parche es MDVA-38393. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.5-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las reglas de catálogo dejan de funcionar para un producto configurable si se cambia el nombre de su producto simple.

<u>Pasos a seguir</u>:

1. Cree un producto configurable con un producto simple asociado.
1. Cree una categoría.
1. Asigne únicamente el producto configurable a la nueva categoría.
1. Crear nuevas reglas de catálogo:
   * Condición = La categoría contiene \&lt;new category=&quot;&quot; id=&quot;&quot;>
   * Acción = 50 % de descuento
   * Activo = Sí
1. Realice una reindexación.
1. Compruebe el producto configurable en el front-end (se debe aplicar el descuento).
1. Compruebe la `catalogrule_product` (el producto simple debe tener un descuento).
1. Vaya al Administrador y cambie el nombre del producto simple. Esto añadiría un registro a la `catalogrule_product_cl` tabla.
1. Ejecute el cron o el `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1` comando.
1. Compruebe la `catalogrule_product` tabla.

<u>Resultados esperados</u>:

El producto configurable tiene un descuento.

<u>Resultados reales</u>:

* Los registros de descuento creados para los productos simples faltan en la variable `catalogrule_product` tabla.
* El producto configurable en el front-end tiene el precio original completo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
