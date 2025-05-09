---
title: "ACSD-55231: error de SKU no encontrado al utilizar la funcionalidad de pedido rápido"
description: Aplique el parche ACSD-55231 para solucionar el problema de Adobe Commerce donde aparece el error *'El SKU no se encontró en el catálogo'* al intentar añadir un producto al carro de compras mediante la funcionalidad de pedido rápido.
feature: Products, Checkout, B2B
role: Admin, Developer
exl-id: 463c2c07-39ec-4b03-81f7-ec2f71f5af76
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-55231: error de SKU no encontrado al utilizar la funcionalidad de pedido rápido

El parche ACSD-55231 corrige el problema en el que se obtiene *&#39;El SKU no se encontró en el error del catálogo&#39;* al intentar agregar un producto al carro de compras mediante la funcionalidad de pedido rápido. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44. El ID del parche es ACSD-55231. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Error al obtener *&#39;el SKU no se encontró en el catálogo&#39;* al buscar productos para agregar al carro de compras mediante la funcionalidad de pedidos rápidos.

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce con módulos B2B.
1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]** y establezca:
   * **[!UICONTROL Enable company]**: *Sí*
   * **[!UICONTROL Enable Shared Catalog]**: *Sí*
   * **[!UICONTROL Enable Quick Order]**: *Sí*
1. Guarde la configuración anterior.
1. Vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** y cree un nuevo catálogo compartido.
1. Vaya a **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** y cree un nuevo cliente:
   * En el campo de grupo, elija el catálogo compartido creado recientemente y establezca *[!UICONTROL Allow remote shopping assistance]* en *Sí*.
1. Genere un producto simple con el SKU *p12*, asócielo con la categoría *c1* y, a continuación, elija el catálogo compartido recién creado en la sección [!UICONTROL Product in Shared Catalog].
1. Ejecutar:

   ```
   bin/magento ind:rei 
   bin/magento c:f 
   bin/magento cron:run (multiple times)
   ```

1. Actualice la página de administración.
1. Vaya a **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** y edite el cliente creado anteriormente.
1. Haga clic en **[!UICONTROL Login as customer]**.
1. Ir a **[!UICONTROL Quick order]**.
1. Busque el SKU *p12* y haga clic en **[!UICONTROL Product Suggestion]**.
1. Añada este producto al carro de compras y haga el pedido.
1. Vuelve a **[!UICONTROL Quick Order]**, busca la SKU *p12* y haz clic en **[!UICONTROL Product Suggestion]**.

<u>Resultados esperados</u>:

Puede añadir el producto al carro de compras mediante la funcionalidad de pedidos rápidos.

<u>Resultados reales</u>:

No puede agregar el producto al carro de compras mediante la funcionalidad de pedido rápido y obtener *&#39;El SKU no se encontró en el error del catálogo&#39;* al buscar el SKU del producto.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
