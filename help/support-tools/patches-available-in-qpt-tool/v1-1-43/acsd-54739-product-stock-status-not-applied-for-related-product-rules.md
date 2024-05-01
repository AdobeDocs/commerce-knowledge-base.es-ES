---
title: 'ACSD-54739: *[!UICONTROL Product Stock]* Estado no solicitado *[!UICONTROL Related Product Rules]*'
description: Aplique el parche ACSD-54739 para solucionar el problema de Adobe Commerce donde *[!UICONTROL Product Stock]* el estado no se ha aplicado a *[!UICONTROL Related Product Rules]*.
feature: Products
role: Admin, Developer
exl-id: 7bc106b1-2c97-46a1-8bb6-71b99511e480
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-54739: *[!UICONTROL Product stock]* estado no aplicado para *[!UICONTROL Related Product Rules]*

El parche ACSD-54739 corrige el problema en el que la variable *[!UICONTROL Product stock]* el estado no se ha aplicado para *[!UICONTROL Related Product Rules]*. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 está instalado. El ID del parche es ACSD-54739. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

*[!UICONTROL Product stock]* el estado no se ha aplicado para *[!UICONTROL Related Product Rules]*.

<u>Pasos a seguir</u>:

1. Configure las variables **[!UICONTROL Display Out of Stock Products]** configuración a *Sí*.
1. Ir a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** > **[!UICONTROL Search quantity attribute]** y establecer *Sí* para la condición de regla de promoción.
1. Cree la regla de producto relacionada. Ir a **[!UICONTROL Product rule information]** > **[!UICONTROL Products to match]** > Añada una condición con la cantidad de atributos (seleccione en stock/sin existencias).
1. Compruebe los productos en la parte delantera.

<u>Resultados esperados</u>:

El producto en stock/sin existencias coincide con el siguiente *[!UICONTROL Related Product Rules]*.

<u>Resultados reales</u>:

El producto en existencia/sin existencias no coincide con el *[!UICONTROL Related Product Rules]*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
