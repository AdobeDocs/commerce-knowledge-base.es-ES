---
title: "ACSD-52736: [!UICONTROL Cart Price Rule] no funciona como se esperaba"
description: Aplique el parche ACSD-52736 para solucionar el problema de Adobe Commerce donde [!UICONTROL Cart Price Rule] que incluye los requisitos para la cantidad de productos configurables no funciona según lo esperado.
feature: Shopping Cart, Products
role: Admin, Developer
exl-id: 8403b418-b197-4695-88a8-e322b18cd4ad
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-52736: [!UICONTROL Cart Price Rule] no funciona como se esperaba

El parche ACSD-52736 corrige el problema en el que un [!UICONTROL Cart Price Rule] que incluye los requisitos para la cantidad de productos configurables no funciona según lo esperado. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.36 está instalado. El ID del parche es ACSD-52736. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

A [!UICONTROL Cart Price Rule] que incluye los requisitos para la cantidad de productos configurables no funciona como se esperaba.

<u>Pasos a seguir</u>:

1. Crear una regla de carro de compras:
   * [!UICONTROL Apply] = Porcentaje de descuento en el precio del producto
   * [!UICONTROL Discount Amount] = 60
   * [!UICONTROL Maximum Qty Discount is Applied to] = 1
   * [!UICONTROL Discount Qty Step (Buy X)] = 1
   * Aplicar la regla solo a los artículos del carro que cumplan las siguientes condiciones: La cantidad del carro es 1
2. Añadir un producto con [!UICONTROL Qty] = 2, al carro de compras.
3. Comprobar precios del carro de compras.

<u>Resultados esperados</u>:

La regla no se aplica porque la cantidad de productos en el carro de compras es *2*.

<u>Resultados reales</u>:

Se aplica el descuento.

<u> Pasos adicionales necesarios tras la instalación del parche</u>:

Después de aplicar el parche, las condiciones de la regla de carro de compras utilizan el *Cantidad* El atributo debe eliminarse y añadirse de nuevo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
