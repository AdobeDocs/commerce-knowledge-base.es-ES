---
title: "ACSD-52399: Producto con cantidad salable 0 se muestra en stock"
description: Aplique el parche ACSD-52399 para solucionar el problema de Adobe Commerce donde la opción de producto configurable con una cantidad escalable de 0 muestra *En stock* en la página del producto.
feature: Products, Configuration
role: Admin, Developer
exl-id: 3c9e6edd-f7ce-492e-b74f-68354d8e2633
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-52399: Producto con cantidad salable 0 muestra en stock

El parche ACSD-52399 corrige el problema en el que se muestra la opción de producto configurable con una cantidad comercializable de cero (0) *En stock* en la página de producto. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.35 está instalado. El ID del parche es ACSD-52399. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La opción de producto configurable con una cantidad escalable de cero (0) muestra *En stock* en la página de producto.

<u>Pasos a seguir</u>:

1. Cree un producto configurable con la opción de producto de cantidad vendible cero (0).
1. Vaya a la página del producto en la tienda y seleccione el producto configurable para comprobar una variación o configuración.
1. Seleccionar **[!UICONTROL Add to Cart]**.

<u>Resultados esperados</u>:

*[!UICONTROL Add to Cart]* El botón no está disponible al seleccionar *Agotado* configuración del producto.

<u>Resultados reales</u>:

Las variaciones configurables están disponibles en la tienda y puede seleccionarlas y agregarlas al carro de compras.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
