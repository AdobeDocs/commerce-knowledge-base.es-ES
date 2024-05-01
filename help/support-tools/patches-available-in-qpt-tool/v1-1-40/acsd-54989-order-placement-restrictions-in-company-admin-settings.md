---
title: 'ACSD-54989: el administrador de la empresa no puede realizar pedidos cuando [!UICONTROL Enable Purchase Orders] establezca en Yes y [!UICONTROL Purchase Order] se establece en No'
description: Aplique el parche ACSD-54989 para solucionar el problema de Adobe Commerce en el que el administrador de la empresa no puede realizar pedidos si [!UICONTROL Enable Purchase Orders] se establece en Yes y [!UICONTROL Purchase Order] se establece en No.
feature: Orders, Companies, Purchase Orders
role: Admin, Developer
exl-id: c2850409-d310-4681-80ec-af8ba347854c
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-54989: el administrador de la empresa no puede realizar pedidos cuando *[!UICONTROL Enable Purchase Orders]* establezca en *Sí* y *[!UICONTROL Purchase Order]* establezca en *No*

El parche ACSD-54989 soluciona el problema de que no se pueden realizar pedidos si **[!UICONTROL Enable Purchase Orders]** establezca en *Sí* y **[!UICONTROL Purchase Order]** establezca en *No*. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 está instalado. El ID del parche es ACSD-54989. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p5 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los administradores de la empresa no pueden realizar pedidos cuando **[!UICONTROL Enable Purchase Orders]** se establece en *Sí* y **Pedido de compra** establezca en *No*.

<u>Requisitos previos</u>:

Instalar [!DNL B2B] módulos.

<u>Pasos a seguir</u>:

1. Activar empresa y salir [!UICONTROL **Order Approval Configuration]** > **[!UICONTROL Purchase Order**] = *No*.
1. Cree un producto simple con un precio de 100.
1. Cree una nueva compañía a través de Admin.
1. Establecer [!UICONTROL **Activar pedidos de compra**] hasta *Sí*.
1. Inicie sesión como administrador de la empresa en la tienda.
1. Añadir el producto simple creado al carro de compras.
1. Vaya a la página de cierre de compra y haga clic en **[!UICONTROL Place Order]** para completar la compra.

<u>Resultados esperados</u>:

Puede realizar un pedido correctamente.

<u>Resultados reales</u>:

El **[!UICONTROL My Account]** se abre la página y no se realiza el pedido.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
