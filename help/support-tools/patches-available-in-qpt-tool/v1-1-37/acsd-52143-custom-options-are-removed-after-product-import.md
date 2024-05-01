---
title: "ACSD-52143: las opciones personalizadas se eliminan después de importar el producto"
description: Aplique el parche ACSD-52143 para corregir el problema de Adobe Commerce en el que las opciones de personalización se eliminan después de importar el producto.
feature: Data Import/Export
role: Admin, Developer
exl-id: 7dde1efe-37a3-443f-9ce1-82cf1b3d9da7
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-52143: las opciones personalizadas se eliminan después de importar el producto

El parche ACSD-52143 corrige el problema en el que las opciones personalizadas se eliminan después de la importación del producto. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.37 está instalado. El ID del parche es ACSD-52143. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p2

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las opciones personalizadas se eliminan después de la importación del producto.

<u>Pasos a seguir</u>:

1. Ir a **[!UICONTROL Store]** > **[!UICONTROL All Stores]** y configure una instancia de varias tiendas (un sitio web con dos vistas de tiendas).
1. Ir a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** y cree dos productos con [!UICONTROL Customizable Options].
1. En cada producto, añada una [!UICONTROL Customizable Option].
1. Cambie a la vista de la segunda tienda y modifique el nombre del producto en cada producto.
1. Ir a **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** y exporte los dos productos que ha creado.
1. Descargue el archivo CSV.
1. Ir a **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** y vuelva a importar el archivo.
1. Compruebe ambos productos.

<u>Resultados esperados</u>:

Las opciones personalizadas no se eliminan después de la importación del producto.

<u>Resultados reales</u>:

Las opciones de aduana se eliminan después de la importación del producto.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
