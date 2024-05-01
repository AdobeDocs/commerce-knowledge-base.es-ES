---
title: "ACSD-54111: La imagen en miniatura del producto no se muestra"
description: Aplique el parche ACSD-54111 para solucionar el problema de Adobe Commerce, donde todas las imágenes se sustituyen por la imagen de marcador de posición de producto predeterminada.
feature: Products
role: Admin, Developer
exl-id: 087786e3-9d61-4fef-8884-8d22fa9170e3
source-git-commit: a863015920917050106ed5d210d0511515807cc7
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-54111: la imagen en miniatura del producto no se muestra

El parche ACSD-54111 soluciona el problema de reemplazar todas las imágenes por la imagen de marcador de posición de producto predeterminada. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38 está instalado. El ID del parche es ACSD-54111. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación): 2.4.5-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación): 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

No se muestra la imagen en miniatura del producto.

<u>Pasos a seguir</u>:

1. Ir a **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]** > **[!UICONTROL Edit Theme]** > **[!UICONTROL Product Image Watermarks]** > **[!UICONTROL Thumbnail]**.
1. Cargue la imagen con una miniatura y establezca la posición de la imagen como *[!UICONTROL Center]*.
1. Haga clic en **[!UICONTROL Save Configuration]**.
1. Borrar caché.
1. Vaya a la tienda como cliente/invitado.
1. Añadir un producto al carro de compras.
1. Ejecutar `bin/magento catalog:image:resize` desde la consola.
1. Abra el minicarrito en el front-end o la cuadrícula de producto en el back-end para ver si las miniaturas de la imagen están visibles.

<u>Resultados esperados</u>:

Las imágenes de producto no se sustituyen por la imagen de marcador de posición.

<u>Resultados reales</u>:

Las imágenes de producto se sustituyen por la imagen de marcador de posición de producto predeterminada.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
