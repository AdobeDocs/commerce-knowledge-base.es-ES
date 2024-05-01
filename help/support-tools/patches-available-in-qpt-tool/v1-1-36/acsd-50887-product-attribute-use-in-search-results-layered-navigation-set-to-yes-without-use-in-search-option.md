---
title: 'ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* se establece en Sí sin *[!UICONTROL Use in Search]* opción'
description: Aplique el parche ACSD-50887 para corregir el problema de Adobe Commerce donde la propiedad de atributos del producto *[!UICONTROL Use in Search Results Layered Navigation]* se puede configurar como *Sí* sin el *[!UICONTROL Use in Search]* opción que también se configura en *Sí*.
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
exl-id: b597709b-7489-41a0-b1ff-d68d0def0b46
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* establezca en *Sí* sin el *[!UICONTROL Use in Search]* opción

El parche ACSD-50887 corrige el problema en el que la propiedad de atributos del producto *[!UICONTROL Use in Search Results Layered Navigation]* se puede establecer en *Sí* sin el *[!UICONTROL Use in Search]* opción que también se configura como *Sí*. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.36 está instalado. El ID del parche es ACSD-50887. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La propiedad de atributos del producto *[!UICONTROL Use in Search Results Layered Navigation]* se puede establecer en *Sí* sin el *[!UICONTROL Use in Search]* opción que también se configura como *Sí*.

Estos ajustes se diseñaron para utilizarse juntos. Con el parche aplicado, al *[!UICONTROL Use in Search]* se establece en *No*, el *[!UICONTROL Use in Search Results Layered Navigation]* está oculta para funcionar como si también estuviera configurada como *No*.

<u>Pasos a seguir</u>:

1. En el Administrador, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Attribute]** > **[!UICONTROL Product]** y cree un atributo con el tipo multiselect y establezca lo siguiente:

   * *[!UICONTROL Use in Search]= No*
   * *[!UICONTROL Use in Layered Navigation]= (Cualquier opción)*
   * *[!UICONTROL Use in Search Results Layered Navigation]= Sí*
   * *Nombre = Atributo_de_prueba*
   * *Opciones*:
      * *Pegatina*
      * *Selector*

1. Agregue el nuevo atributo al conjunto de atributos predeterminado.
1. Cree dos productos:

   1. Primer producto:
      * Nombre = Etiqueta
      * Establecer precio, cantidad, peso en 1
      * Test_attribute = seleccionar opción *Pegatina*

   1. Segundo producto:
      * Nombre = Selector
      * Establecer precio, cantidad, peso en 1
      * Atributo_prueba = seleccionar ambas opciones

1. Ejecutar `catalogsearch_fulltext` reindexar:

   `bin/magento indexer:reindex catalogsearch_fulltext`

1. Buscar por la palabra *etiqueta engomada* en la tienda.

<u>Resultados esperados</u>:

Solo el producto *Pegatina* se devuelve, porque [!DNL Elasticsearch] no indexará Test_attribute cuando *[!UICONTROL Use in Search]* se ha establecido en *No*.

<u>Resultados reales</u>:

Se devuelven ambos productos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
