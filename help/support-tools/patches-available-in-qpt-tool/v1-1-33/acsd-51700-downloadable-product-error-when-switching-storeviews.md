---
title: "ACSD-51700: Error al cambiar las vistas de tienda en la página de edición de productos descargable"
description: Aplique el parche ACSD-51700 para corregir el problema de Adobe Commerce donde se produce un error al cambiar de vista de tienda en una página de edición de producto descargable en el administrador.
feature: Products
role: Admin
exl-id: 652876a5-275d-437f-9cb3-baf4e7b23aae
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51700: Error al cambiar las vistas de tienda en la página de edición descargable del producto

El parche de ACSD-51700 corrige el problema en el que se produce un error al cambiar de vista de tienda en una página de edición de producto descargable en el administrador. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.33. El ID del parche es ACSD-51700. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6-p1

## Problema

Se produce un error al cambiar las vistas de la tienda en una página de edición de productos descargable en el administrador.

<u>Pasos a seguir</u>:

1. Cree un producto descargable con el nombre [!DNL SKU] y el precio. No añada ningún vínculo y guarde el producto.
1. Cambie de todas las vistas de tienda a la vista de tienda predeterminada.
1. Cree un vínculo para el producto descargable y guárdelo.
1. Cambie de la vista de tienda predeterminada a todas las vistas de tienda.

<u>Resultados esperados</u>:

Los productos vinculados están visibles.

<u>Resultados reales</u>:

Se muestra el siguiente error:

*Funcionalidad obsoleta: number_format(): Pasar nulo al parámetro #1 ($num) del tipo float está obsoleto en vendor/magento/module-downloadable/Ui/DataProvider/Product/Form/Modifier/Data/Links.php en la línea 228*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
