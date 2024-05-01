---
title: 'ACSD-53925: No se puede guardar el bloque CMS con [!UICONTROL Product Carousel]'
description: Aplique el parche ACSD-53925 para solucionar el problema de Adobe Commerce en el que el administrador no puede guardar un bloque CMS con el carrusel de productos cuando el modo de dimensiones para catalog_product_price está establecido en un sitio web.
feature: CMS, Page Builder, Price Indexer, Products
role: Admin, Developer
exl-id: 6ef6d8ff-4ebb-4adb-9fb7-0d4a81a25f50
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-53925: No se puede guardar el bloque CMS con *[!UICONTROL Product Carousel]*

El parche ACSD-53925 corrige el problema en el que el administrador no puede guardar un bloque CMS con *[!UICONTROL Product Carousel]* cuando el modo de dimensiones para `catalog_product_price` se establece en sitio web. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.43 está instalado. El ID del parche es ACSD-53925. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El administrador no puede guardar un bloque CMS con *[!UICONTROL Product Carousel]* cuando el modo de dimensiones para `catalog_product_price` se establece en sitio web.

<u>Pasos a seguir</u>:

1. Cree dos productos simples:
   * simple1 - $10
   * simple2 - $20
1. Crear un producto del paquete &#39;*bundle1-dyn*&#39; con dos opciones basadas en SKU de productos simples.
1. Establezca el modo de dimensiones para el indexador de precios del producto:

   `bin/magento indexer:set-dimensions-mode catalog_product_price website`

1. Ir a **[!UICONTROL Content]** > **[!UICONTROL Blocks]** y cree un nuevo bloque de CMS.
1. Edición del contenido mediante [!DNL Page Builder]:
   * Añadir un *[!UICONTROL Row]* elemento
   * Añadir un *[!UICONTROL Products]* elemento
   * Seleccionar *[!UICONTROL Product Carousel]*
   * Introducir SKU del producto - *bundle1-dyn*
1. Guarde el bloque CMS.

<u>Resultados esperados</u>:

El usuario puede añadir un carrusel de productos sin errores.

<u>Resultados reales</u>:

* Se envía un mensaje en la interfaz de usuario de: *Se ha producido un error al generar este contenido*
* `var/log/exception.log` contiene el siguiente error:

  ```
  [2023-08-18T20:58:14.533374+00:00] report.CRITICAL: PDOException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'username_dev.catalog_product_index_price_ws0' doesn't exist in /test/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
  ```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
