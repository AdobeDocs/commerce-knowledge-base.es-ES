---
title: "ACSD-52160: resultado de validación del producto frente a la regla de precio del carro de compras"
description: Aplique el parche ACSD-52160 para corregir el problema de Adobe Commerce en el que el resultado de validación del producto con la regla de precio del carro de compras no se evalúa correctamente en función de la condición de regla *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*.
exl-id: a371c539-4440-4c84-baa4-774c32f66e41
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-52160: el resultado de validación del producto frente a la regla de precio del carro de compras no se evalúa correctamente

El parche ACSD-52160 corrige el problema en el que el resultado de validación del producto frente a la regla de precio del carro de compras no se evalúa correctamente en función de la condición de regla *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34. El ID del parche es ACSD-52160. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El resultado de validación del producto frente a la regla de precio del carro de compras no se evalúa correctamente según la condición de regla *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*.

<u>Pasos a seguir</u>:

1. Cree dos productos asignados a dos categorías diferentes.
1. Crear un(a) **[!UICONTROL Cart Price Rule]** con condiciones como:

   * **SKU 1** en el parámetro *[!UICONTROL FOUND]*
   * **SKU 2** en el parámetro *[!UICONTROL NOT FOUND]*

1. Agregue ambos productos al carro de compras.
1. Aplique el código de cupón.

<u>Resultados esperados</u>

El código de cupón no se aplica porque el carrito contiene productos de la categoría restringida.

<u>Resultados reales</u>

Se aplica el código de cupón.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) en la guía [!DNL Quality Patches Tool].
