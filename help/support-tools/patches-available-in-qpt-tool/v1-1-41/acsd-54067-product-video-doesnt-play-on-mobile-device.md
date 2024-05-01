---
title: "ACSD-54067: El vídeo del producto no se reproduce en el dispositivo móvil"
description: Aplique el parche ACSD-54067 para corregir el problema de Adobe Commerce en el que un vídeo del producto no se reproduce en un dispositivo móvil.
feature: Media, Products
role: Admin, Developer
exl-id: 369650ef-bcce-47c5-bbfe-39f3c2b1d73f
source-git-commit: 0795e3e0ba11002c8aff2794e16fa05f1c7e19c3
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-54067: El vídeo del producto no se reproduce en un dispositivo móvil

El parche ACSD-54067 soluciona el problema de que el vídeo de un producto no se reproduce en un dispositivo móvil. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 está instalado. El ID del parche es ACSD-54067. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El vídeo de un producto no se reproduce en un dispositivo móvil.

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce.
1. Ejecute el comando:
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Ir a **[!UICONTROL Admin product list]** página y filtro por *[!UICONTROL SKU product_dynamic_120]*.
1. Abra la página del producto y vaya a **[!UICONTROL Images and Videos]** > añada un vídeo > complete la URL: https://vimeo.com/347119375 y guarde.
1. Vaya a la tienda y abra la página de producto de *[!UICONTROL product_dynamic_120]*.
1. Configure el explorador como *dispositivo móvil* con una anchura de *320px* y actualice.
1. En el deslizador de la galería, seleccione el vídeo y haga clic en para reproducirlo.

<u>Resultados esperados</u>:

Se reproduce el vídeo del producto.

<u>Resultados reales</u>:

El vídeo del producto no se reproduce.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
