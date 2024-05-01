---
title: "ACSD-54680: no se puede procesar la cotización B2B de un producto con varias fuentes asignadas"
description: Aplique el parche ACSD-54680 para solucionar el problema de Adobe Commerce en el que no se puede procesar la cotización B2B de un producto con varios orígenes asignados.
feature: B2B
role: Admin, Developer
exl-id: 4d05714c-d32d-46f3-b857-81704c9e96cd
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# ACSD-54680: la cotización B2B de un producto con varios orígenes asignados no se puede procesar.

El parche ACSD-54680 soluciona el problema que impedía procesar el presupuesto B2B de un producto con varias fuentes asignadas. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.40 está instalado. El ID del parche es ACSD-54680. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La cotización B2B de un producto con varios orígenes asignados no se puede procesar.

<u>Pasos a seguir</u>:

1. Ir a **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Sources]** y cree dos nuevas fuentes: **Origen 1** y **Origen 2**.
1. Ir a **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Stocks]** y cree un nuevo Stock: **Stock A**, asígnelo al sitio web principal y asigne **Origen 1** y **Origen 2** a ella.
1. Crear un producto simple, asignar **Origen 1** y **Origen 2** y establezca Cantidad = *2* para cada origen. (la cantidad salable del producto debe ser *4* como resultado).
1. Crear una cuenta de compañía.
1. Vaya a la **[!UICONTROL Storefront]** e inicie sesión en su cuenta de empresa.
1. Añada el producto simple al carro de compras con la cantidad = *4*.
1. Abra el *[!UICONTROL Shopping cart]* y haga clic en **[!UICONTROL Request a quote]** botón.
1. Añada un comentario y un nombre de presupuesto y haga clic en **[!UICONTROL Send a Request]** botón.
1. Ir a **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.
1. Abrir oferta enviada recientemente.

<u>Resultados esperados</u>:

Los artículos citados contienen el producto pedido.

<u>Resultados reales</u>:

La sección de la página de artículos citados está vacía y no es posible procesar el presupuesto.
`var/log/system.log` contains

```
report.CRITICAL: TypeError: number_format() expects parameter 1 to be float, null given in .../vendor/magento/module-negotiable-quote/Model/QuoteUpdatesInfo.php:232
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
