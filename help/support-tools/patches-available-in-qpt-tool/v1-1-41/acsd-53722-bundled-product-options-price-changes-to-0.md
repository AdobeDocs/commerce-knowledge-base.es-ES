---
title: "ACSD-53722: el precio de las opciones de productos agrupadas cambia a 0 $"
description: Aplique el parche ACSD-53722 para corregir el problema de Adobe Commerce en el que el precio de las opciones del producto agrupadas cambia a 0 $ cuando se activan actualizaciones programadas para diferentes ámbitos.
feature: Products
role: Admin, Developer
exl-id: da4c25ac-78bc-4d4e-a55e-826924a099e9
source-git-commit: e587b70a270bca624fb60a1b0940c05221da3aef
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-53722: el precio de las opciones de productos agrupadas cambia a 0 $

El parche ACSD-53722 corrige el problema en el que el precio de las opciones del producto empaquetado cambia a 0 $ cuando se activan actualizaciones programadas para diferentes ámbitos. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41. El ID del parche es ACSD-53722. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El precio de las opciones de productos agrupados cambia a 0 $ cuando se activan las actualizaciones programadas para diferentes ámbitos.

<u>Pasos a seguir</u>:

1. Cree dos sitios web, A y B.
1. Establecer configuración en **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]** = **[!UICONTROL Website]**.
1. Cree un producto agrupado con un precio fijo en los sitios web A y B:

   * Precio del producto agrupado = fijo = *0*

1. Añada un producto simple como opción desplegable para el paquete. Fije los siguientes precios:

   * Precio de todas las vistas de la tienda del producto simple dentro de la opción agrupada = *120*
   * Sitio web del producto simple Precio dentro de la opción agrupada = *130*
   * Precio del sitio web B del producto simple dentro de la opción agrupada = *140*

1. Programe una actualización para deshabilitar el producto agrupado en el sitio web A.

<u>Resultados esperados</u>:

La actualización programada para el sitio A no afecta al precio del sitio B.

<u>Resultados reales</u>:

Después de la actualización programada, el precio de la opción de producto empaquetado en el sitio web B se cambió a **$0**.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
