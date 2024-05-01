---
title: "ACSD-51884: Ruta incorrecta de la caché de imágenes de producto en el comando resize"
description: Aplique el parche ACSD-51884 para corregir el problema de Adobe Commerce en el que la ruta de acceso de la caché de la imagen del producto se vuelve incorrecta después de ejecutar el comando resize.
feature: Products
role: Admin
exl-id: cf542c4b-07b1-4f05-95bc-82bc098bcd4d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-51884: ruta incorrecta de la caché de imágenes de producto en el comando resize

El parche ACSD-51884 corrige el problema de un error interno en el que la ruta de la caché de la imagen del producto se vuelve incorrecta después de ejecutar el comando de cambio de tamaño. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.37 está instalado. El ID del parche es ACSD-51884. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7-2.4.7

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La ruta de acceso a la caché de imágenes de producto es incorrecta con el comando resize.

<u>Pasos a seguir</u>:

1. Crear nuevo sitio web, tienda o vista de tienda.
1. Cree un producto, asígnelo a ambos sitios web y cargue la imagen del producto.
1. Crear una temática nueva (consulte el Adobe adjunto.zip).
1. Entrada `app/design/Adobe/theme/etc/view.xml` cambiar:

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">1</var>
</vars>
```

hasta

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">0</var>
</vars>
```

1. Aplique la temática a la vista de tienda creada anteriormente.
1. Consulte la página del producto en el segundo sitio web. La imagen del producto se muestra correctamente.
1. Usar caché de vaciado:
   `bin/magento cache:flush`
1. Consulte la página del producto en el segundo sitio web.

<u>Resultados esperados</u>:

La imagen del producto se muestra correctamente.

<u>Resultados reales</u>:

La imagen del producto no existe.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
