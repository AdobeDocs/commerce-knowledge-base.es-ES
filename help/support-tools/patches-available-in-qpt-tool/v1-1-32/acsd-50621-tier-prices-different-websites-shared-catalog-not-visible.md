---
title: "ACSD-50621: Los precios de nivel de diferentes sitios web en el catálogo compartido no son visibles"
description: Aplique el parche ACSD-50621 para corregir el problema de Adobe Commerce en el que los precios de nivel de diferentes sitios web en el catálogo compartido no son visibles al editarlos en un entorno de varios sitios web.
exl-id: 6d6635bc-4f76-4e2f-9bc7-0276cced8ca9
feature: Catalog Management, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-50621: Los precios de nivel de diferentes sitios web en el catálogo compartido no son visibles

El parche ACSD-50621 soluciona el problema de que los precios de nivel de los distintos sitios web del catálogo compartido no son visibles al editarlos en un entorno de varios sitios web. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.32 está instalado. El ID del parche es ACSD-50621. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los precios de nivel de diferentes sitios web en el catálogo compartido no son visibles al editarlos en un entorno de varios sitios web.

<u>Pasos a seguir</u>:

1. Configure las variables **[!UICONTROL Catalog Price Scope]** hasta **[!UICONTROL Website]**.
1. Cree un sitio web, una tienda y una vista de tienda adicionales.
1. Cree un producto simple y asígnelo a todos los sitios web.
1. Cree un catálogo compartido personalizado.
1. Ir a **[!UICONTROL Set Pricing and Structure]** para el catálogo compartido personalizado que ha creado.
1. En el paso 1: seleccione los productos para el catálogo. Añada el producto simple que ha creado.
1. En el paso 2: establezca los precios personalizados y haga clic en **[!UICONTROL Configure]**.
1. Establece diferentes niveles de precios para diferentes sitios web.
1. Seleccionar **[!UICONTROL Done]** y haga clic en **[!UICONTROL Generate Catalog]** y luego haga clic en **[!UICONTROL Save]**.
1. Corre cron.
1. Vaya a **[!UICONTROL Set Pricing and Structure]** > **[!UICONTROL Configure]** > **[!UICONTROL Next]** > **[!UICONTROL Configure]** y verifique el precio del nivel.

<u>Resultados esperados</u>:

Están presentes todos los precios de nivel configurados previamente para diferentes sitios web.

<u>Resultados reales</u>:

Los precios de nivel que se configuraron anteriormente no están presentes.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
