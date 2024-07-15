---
title: "MDVA-31763: Las reglas de precios de catálogo se revierten hasta la reindexación manual"
description: El parche MDVA-31763 resuelve el problema en el que las reglas de precios de catálogo se revierten hasta la reindexación manual. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5. El ID del parche es MDVA-31763. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: eb2dfd1a-6d12-4676-82c1-bf92c6fa9fda
feature: Catalog Management, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-31763: Las reglas de precios de catálogo se revierten hasta la reindexación manual

El parche MDVA-31763 resuelve el problema en el que las reglas de precios de catálogo se revierten hasta la reindexación manual. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5. El ID del parche es MDVA-31763. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando se ejecuta el indexador parcial `catalogrule_product` en productos configurables, las reglas del catálogo desaparecen.

<u>Pasos a seguir</u>:

1. Inicie sesión en el servidor de administración.
1. Vaya a **Tiendas** > **Atributos** > **Producto** y busque el atributo &quot;fabricante&quot;.
   * Agregue algunas opciones y establezca &quot;Usar para condiciones de regla de promoción&quot; en *Sí*.
1. Vaya a **Tiendas** > **Atributos** > **Conjuntos de atributos**.
   * Seleccione el conjunto de atributos predeterminado y agréguele el atributo &quot;manufacturer&quot;.
1. Cree un producto configurable con un par de variaciones.
1. Establezca el valor de atributo &quot;fabricante&quot; para el producto configurable creado anteriormente.
1. Crear reglas de catálogo:
   * Activo = Sí
   * Sitios web = Sitio web principal
   * Grupos de clientes = SIN SESIÓN INICIADA
   * Condiciones: fabricante = \&lt;valor seleccionado para el producto configurable>
   * Acciones: cualquier descuento
1. Haga un índice completo.
1. Compruebe el precio del producto en PDP y asegúrese de que el precio es correcto.
1. Actualice el atributo &quot;weight&quot; del producto configurable creado.
1. Compruebe el precio del producto en PDP.

<u>Resultados esperados</u>:

Las reglas de precios de catálogo establecidas en los productos configurables no se eliminan durante el reindexado parcial.

<u>Resultados reales</u>:

Las reglas de precios de catálogo establecidas en los productos configurables desaparecen durante el reindexado parcial.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
