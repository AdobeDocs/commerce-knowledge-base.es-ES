---
title: "ACSD-52398: la cantidad solicitada no está disponible al intentar actualizar la cantidad del producto agrupado"
description: Aplique el parche ACSD-52398 para solucionar el problema de Adobe Commerce en el que la cantidad solicitada no está disponible al intentar actualizar la cantidad de un producto agrupado en el carro de compras de la tienda.
feature: Shopping Cart, Quotes, Products
role: Admin
exl-id: 7b7f06ac-7913-4603-992a-a5620045d828
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-52398: la cantidad solicitada no está disponible al intentar actualizar la cantidad del producto agrupado

El parche ACSD-52398 corrige el problema en el que la cantidad solicitada no está disponible al intentar actualizar la cantidad de un producto agrupado en el carro de compras de la tienda. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.35 está instalado. El ID del parche es ACSD-52398. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La cantidad solicitada no está disponible al intentar actualizar la cantidad de un producto agrupado en el carro de compras en la tienda.

<u>Pasos a seguir</u>:

1. Cree dos productos simples con cantidad *1* y *10*.
1. Cree un producto agrupado con los productos simples.
1. Añadir el producto agrupado al carro de compras.
1. Edite el producto e intente actualizar la cantidad a *3* para la opción donde *10* Hay elementos disponibles.

<u>Resultados esperados</u>:

No hay ningún error. La cantidad se ha actualizado correctamente porque hay *10* artículos en stock para esta opción.

<u>Resultados reales</u>:

Se genera el siguiente error: *La cantidad solicitada no está disponible*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
