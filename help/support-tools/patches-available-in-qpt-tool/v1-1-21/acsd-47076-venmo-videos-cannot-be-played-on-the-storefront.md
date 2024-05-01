---
title: '''ACSD-47076: [!DNL Vimeo] los vídeos no se pueden reproducir en la tienda"'
description: Aplique el parche ACSD-47076 para solucionar el problema de Adobe Commerce donde [!DNL Vimeo] los vídeos no se pueden reproducir en la tienda.
exl-id: 52161c0d-3d51-45a3-ba41-36f955df0bea
feature: Storefront
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-47076: [!DNL Vimeo] no se pueden reproducir vídeos en la tienda

El parche ACSD-47076 corrige el problema donde [!DNL Vimeo] los vídeos no se pueden reproducir en la tienda. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 está instalado. El ID del parche es ACSD-47076. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.3-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

[!DNL Vimeo] los vídeos no se pueden reproducir en la tienda.

<u>Pasos a seguir</u>:

1. Añadir un [!DNL Vimeo] Vídeo a un producto en Commerce [!UICONTROL Admin] > **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > página de edición del producto > **[!UICONTROL Images and Videos]**.
1. Abra el producto en la tienda y reproduzca el vídeo.

<u>Resultados esperados</u>:

El [!DNL Vimeo] se puede reproducir el vídeo.

<u>Resultados reales</u>:

El [!DNL Vimeo] el vídeo no se puede reproducir en la tienda.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
