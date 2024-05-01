---
title: '''ACSD-54965: [!UICONTROL Visual Merchandising] la rejilla no muestra el stock correcto"'
description: Aplique el parche ACSD-54965 para solucionar el problema de Adobe Commerce donde la variable [!UICONTROL Visual Merchandising] la cuadrícula no muestra las existencias correctas cuando se asigna un producto a las existencias personalizadas.
feature: Merchandising, Categories
role: Admin, Developer
exl-id: 13d98f55-ca2c-4064-b66f-ab2cdeb37382
source-git-commit: 4f05117aa42dec1f56e4986ffd22d1a68bf5cea2
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-54965: [!UICONTROL Visual Merchandising] la cuadrícula no muestra las existencias correctas

El parche ACSD-54965 corrige el problema en el que la variable [!UICONTROL Visual Merchandising] la cuadrícula no muestra las existencias correctas cuando se asigna un producto a las existencias personalizadas. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 está instalado. El ID del parche es ACSD-54965. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El [!UICONTROL Visual Merchandising] la cuadrícula no muestra las existencias correctas cuando se asigna un producto a las existencias personalizadas.

<u>Pasos a seguir</u>:

1. Cree una nueva fuente.
1. Cree un nuevo inventario de stock.
1. Cree dos productos:
   * Un producto solo con el stock personalizado.
   * Un producto solo con las existencias predeterminadas.
1. Añada estos productos a una categoría.
1. Vaya a la [!UICONTROL visual Merchandising] cuadrícula (*[!UICONTROL Products in Category]*).

<u>Resultados reales</u>:

En el *[!UICONTROL All Store Views]* ámbitos, el producto con existencias personalizadas no muestra ninguna cantidad. Es solo cuando la variable *[!UICONTROL Default Store View]* ámbito seleccionado, el stock personalizado muestra la cantidad del producto.

<u>Resultados esperados</u>:

La cuadrícula muestra toda la información de stock si el ámbito es *[!UICONTROL All Store Views]*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
