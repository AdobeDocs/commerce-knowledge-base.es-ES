---
title: "ACSD-54018: Problema de rendimiento con la lista de productos del widget de catálogo"
description: Aplique el parche ACSD-54018 para corregir el problema de Adobe Commerce en el que la página se carga lentamente al añadir una lista de productos de widget de catálogo con condición y tipo de atributo booleano.
feature: Attributes, Catalog Management, Page Builder, Page Content, Storefront
role: Admin, Developer
exl-id: 9f20484d-58c7-49d8-87df-1eeb84bee6fe
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-54018: problema de rendimiento con la lista de productos del widget de catálogo

El parche ACSD-54018 corrige el problema en el que la página se carga lentamente al añadir una lista de productos de widget de catálogo con condición y tipo de atributo booleano. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38 está instalado. El ID del parche es ACSD-54018. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La página se carga lentamente al añadir una lista de productos de widget de catálogo con condición y tipo de atributo booleano.

<u>Pasos a seguir</u>:

1. Genere 100k productos.
1. Cree un atributo bool con el ámbito establecido en [!UICONTROL Store View].
1. Asignar atributo a todos los conjuntos de atributos.
   * Asignar el valor del atributo *Sí* a todos los productos.
1. Ahora, vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** y seleccione los 100.000 productos.
   * Elegir **[!UICONTROL Actions]** > **[!UICONTROL Update Attribute]**.
   * Establezca el atributo bool en *Sí* y guárdelo.
   * Si ha cerrado la sesión en este paso, consulte *Notas*.
1. Vaya a CLI y ejecute `php bin/magento queue:con:start product_action_attribute.update`.
   * Asegúrese de que se actualizan los atributos de todos los productos.
1. Ahora, vaya a **[!UICONTROL Content]** > **[!UICONTROL Pages]** y cree una nueva página.
1. Abrir **[!UICONTROL Page Builder]** > **[!UICONTROL Add row]** > **[!UICONTROL Add Content]** > **[!UICONTROL Products]**.
1. Elegir *[!UICONTROL Select Products By]* = *[!UICONTROL Condition]*.
1. Configuración de la condición *[!UICONTROL Created attribute]* hasta *[!UICONTROL Yes]* y guárdelo.
1. Vaya al front-end y abra la página creada.
1. Deshabilite la memoria caché de la página completa y bloquee la memoria caché html.
1. Compruebe la velocidad de carga de la página.
1. Vuelva a cargar la página unas cuantas veces y calcule el tiempo medio de carga.

<u>Resultados esperados</u>:

La página se carga rápido.

<u>Resultados reales</u>:

La página tarda de 5 a 10 segundos en cargarse.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
