---
title: "ACSD-49286: producto añadido dos veces al carro de compras cuando hay varios widgets de producto presentes"
description: Aplique el parche ACSD-49286 para corregir el problema de Adobe Commerce por el que el producto se agrega dos veces al carro de compras cuando hay varios widgets de producto en la página.
exl-id: b1764943-945d-4ef9-9bbe-3f3c8383b5b1
feature: Admin Workspace, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-49286: producto añadido dos veces al carro de compras cuando hay varios widgets de producto presentes.

El parche ACSD-49286 corrige el problema de que el producto se agrega dos veces al carro de compras cuando hay varios widgets de producto en la página. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28. El ID del parche es ACSD-49286. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El producto se agrega dos veces a un carro de compras cuando hay varios widgets de producto en la página.

<u>Pasos a seguir</u>:

1. Inicie sesión en el administrador y vaya a **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Page]** > **[!UICONTROL Home Page]**
1. En la sección de contenido, haga clic en **[!UICONTROL Edit]** con [!DNL Page Builder].
1. Agregar dos elementos de fila a **[!UICONTROL Content]**.
1. Agregue productos a ambos elementos de fila.
1. En la primera fila, establezca el aspecto del producto como [!UICONTROL Product Grid] y seleccione cualquier categoría que desee mostrar.
1. En la segunda fila, establezca el aspecto del producto como [!UICONTROL Product Carousel] y seleccione cualquier otra categoría que desee mostrar.
1. Vaya a la tienda **[!UICONTROL Home Page]** y agregue un producto desde la cuadrícula de productos.
1. Agregar otro producto de [!UICONTROL Product Carousel].

<u>Resultados esperados</u>:

La cantidad de productos no debe duplicarse después de agregar un producto al carro de compras de [!UICONTROL Product Grid].

<u>Resultados reales</u>:

La cantidad de productos se duplica después de agregar un producto al carro de compras desde [!UICONTROL Product Grid].

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube. 

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
