---
title: "ACSD-50813: el administrador no puede añadir productos agrupados que contengan una barra oblicua"
description: Aplique el parche ACSD-50813 para solucionar el problema de rendimiento de Adobe Commerce en el que el administrador no puede añadir productos agrupados que contengan una barra diagonal (`/`) en el SKU con la funcionalidad *Añadir productos por SKU* al pedido del administrador.
exl-id: 80dfe877-9dfd-44a9-9bf0-37e929642fc0
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-50813: el administrador no puede añadir productos agrupados que contengan una barra oblicua

El parche ACSD-50813 corrige el problema en el que el administrador no puede añadir productos agrupados que contengan una barra diagonal (`/`) en el SKU con *[!UICONTROL Add Products by SKU]* al orden de administración. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.34 está instalado. El ID del parche es ACSD-50813. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El administrador no puede añadir productos agrupados que contengan una barra diagonal (`/`) en el SKU con *[!UICONTROL Add Products by SKU]* al orden de administración.

<u>Pasos a seguir</u>:

1. Ir a **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Cree un producto sencillo.
1. Cree un nuevo producto agrupado.
1. Agregar una barra diagonal (`/`) en medio del SKU (ejemplo: *Bu/ndle*).
1. Añadir una opción agrupada con **[!UICONTROL Input Type]** = *[!UICONTROL Dropdown]*.
1. Asigne al menos un producto simple a la opción.
1. Ir a **[!UICONTROL Sales]** > **[!UICONTROL Orders]** y cree un nuevo pedido.
1. Haga clic en **[!UICONTROL Add Products by SKU]**.
1. Introduzca su SKU y haga clic en **[!UICONTROL Add to Order]**.
1. Abra la consola del explorador.
1. Haga clic en **[!UICONTROL Configure]**.

<u>Resultados esperados</u>:

No hay ningún error.

<u>Resultados reales</u>:

Error de JS en la consola:

*Error no capturado: Error de sintaxis, expresión no reconocida: div[id=sku_bu/ndle]*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
