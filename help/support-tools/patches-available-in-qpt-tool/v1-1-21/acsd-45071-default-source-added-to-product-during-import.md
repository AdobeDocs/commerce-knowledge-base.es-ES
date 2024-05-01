---
title: "ACSD-45071: origen predeterminado agregado al producto durante la importación"
description: El parche ACSD-45071 soluciona el problema de añadir el origen predeterminado al producto durante la importación. Este parche está disponible cuando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 está instalado. El ID del parche es ACSD-45071. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.
exl-id: 8d8dbb06-6133-4d7a-939a-8bf18caec81c
feature: Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-45071: origen predeterminado añadido al producto durante la importación

El parche ACSD-45071 soluciona el problema de añadir el origen predeterminado al producto durante la importación. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 está instalado. El ID del parche es ACSD-45071. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.3-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Después de una importación de producto, el origen predeterminado se asigna automáticamente al producto, la cantidad se establece en cero y el estado se establece en agotado.

<u>Pasos a seguir</u>:

1. Cree una nueva fuente.
1. Cree un nuevo stock con el nuevo origen.
1. En la página de edición del producto de Adobe Commerce Admin, asigne solo las existencias personalizadas, establezca una cantidad y un estado de existencias **[!UICONTROL In Stock]**.
1. Importe el producto mediante **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]**.

<u>Resultados esperados</u>:

El origen predeterminado no se asigna automáticamente al producto después de la importación.

<u>Resultados reales</u>:

El origen predeterminado se asigna al producto después de importarlo, con un estado sin existencias y una cantidad cero.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
