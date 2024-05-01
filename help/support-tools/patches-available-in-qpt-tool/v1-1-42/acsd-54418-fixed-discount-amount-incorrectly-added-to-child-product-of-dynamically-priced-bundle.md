---
title: "ACSD-54418: cantidad de descuento fija añadida incorrectamente al producto secundario del paquete de precio dinámico"
description: Aplique el parche ACSD-54418 para corregir el problema de Adobe Commerce en el que la cantidad de descuento fija se aplica incorrectamente a cada producto secundario del paquete de precio dinámico.
feature: Shopping Cart
role: Admin, Developer
exl-id: f9a00a4b-0a57-4a61-8b7c-6385e0751991
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-54418: cantidad de descuento fija añadida incorrectamente al producto secundario del paquete de precio dinámico.

El parche ACSD-54418 corrige el problema en el que la cantidad de descuento fija se aplica incorrectamente a cada producto secundario del paquete de precio dinámico. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.42 está instalado. El ID del parche es ACSD-54418. Tenga en cuenta que el problema se corrige en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El importe de descuento fijo se aplica incorrectamente a cada producto secundario del paquete de precios dinámicos.

<u>Pasos a seguir</u>:

1. Crear un **[!UICONTROL bundle product]** con precios dinámicos y *2* opciones de paquete.
1. Crear un **[!UICONTROL cart price rule]** con un código de cupón específico que solo se aplica al producto agrupado **[!UICONTROL SKU]** y tiene un descuento fijo.
1. Añadir el producto agrupado al carro de compras.
1. Aplique la variable **[!UICONTROL coupon code]**.
1. Compruebe el descuento aplicado al carro de compras.

<u>Resultados esperados</u>:

El descuento se aplica solo una vez a todo el producto agrupado.

<u>Resultados reales</u>:

El descuento se aplica a cada paquete de producto secundario.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
