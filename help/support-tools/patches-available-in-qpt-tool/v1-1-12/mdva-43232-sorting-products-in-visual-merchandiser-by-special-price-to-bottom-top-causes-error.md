---
title: "MDVA-43232: La ordenación de productos en el comerciante visual por precio especial a superior (o inferior) provoca un error"
description: El parche de MDVA-43232 soluciona el problema de que la clasificación de productos en Visual Merchandiser por Precio especial al principio (o al final) provoca un error al guardar la categoría. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. El ID del parche es MDVA-43232. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: e958a219-5e93-4ae4-94cb-f478f82ad060
feature: Categories, Merchandising, Orders, Personalization, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# MDVA-43232: La ordenación de productos en el comerciante visual por precio especial a superior (o inferior) causa un error

El parche de MDVA-43232 soluciona el problema de que la clasificación de productos en Visual Merchandiser por Precio especial al principio (o al final) provoca un error al guardar la categoría. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. El ID del parche es MDVA-43232. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.4 - 2.4.3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La ordenación de productos en el comerciante visual por Precio especial al principio (o al final) provoca un error al guardar la categoría.

<u>Pasos a seguir</u>:

1. Asegúrese de que haya dos sitios web.
1. Vaya a **Tiendas** > **Configuración** > **Catálogo** > **Precio** y establezca el ámbito del precio del catálogo = Sitio web.
1. De nuevo, vaya a **Tiendas** > **Configuración** > **Catálogo** > **Comerciante visual** > **Atributos visibles para reglas de categoría** > y agregue Precio especial.
1. Cree un producto sencillo y asígnelo a ambos sitios web.
1. Agregue un precio especial al ámbito predeterminado del producto.
1. Cambie al ámbito de la otra tienda y anule el precio y el precio especial de ese producto.
1. Realice un reindexado de `catalog_product_price`.
1. Vaya a **Catálogo** > **Categorías** y cree una nueva categoría.
1. Añada una regla de categoría para filtrar los productos que tienen un precio especial.
1. Guarde la categoría.
1. En la sección Productos en categoría, establezca Orden = Precio especial en Superior (o Inferior).
1. Vuelva a guardar la categoría.

<u>Resultados esperados</u>:

La categoría se guarda sin errores.

<u>Resultados reales</u>:

Se genera una excepción:

```php
[2022-02-07T05:58:46.297621+00:00] report.CRITICAL: Exception: Item (Magento\Catalog\Model\Product\Interceptor) with the same ID "1" already exists. in /lib/internal/Magento/Framework/Data/Collection.php:407
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/usage) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en nuestra documentación para desarrolladores.
