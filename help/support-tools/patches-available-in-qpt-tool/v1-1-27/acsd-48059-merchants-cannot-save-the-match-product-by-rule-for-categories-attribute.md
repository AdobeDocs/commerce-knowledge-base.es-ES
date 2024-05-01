---
title: '''ACSD-48059: los comerciantes no pueden guardar [!UICONTROL Match product by rule] para el atributo Categories."'
description: Aplique el parche ACSD-48059 para solucionar el problema de Adobe Commerce en el que los comerciantes no pueden guardar los cambios [!UICONTROL Match product by rule] para el atributo Categories.
exl-id: 97213157-1b54-4634-9c76-c9ab8fa96e17
feature: Admin Workspace, Attributes, Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-48059: los comerciantes no pueden guardar la variable *[!UICONTROL Match product by rule]* para el atributo categories

El parche de ACSD-48059 corrige el problema en el que los comerciantes no pueden guardar la *[!UICONTROL Match product by rule]* para el atributo categories en [!DNL Visual Merchandiser]. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 está instalado. El ID del parche es ACSD-48059. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) >=2.3.7 &lt;2.4.7

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los comerciantes no pueden guardar *[!UICONTROL Match product by rule]* para el atributo categories en [!DNL Visual Merchandiser].

<u>Pasos a seguir</u>:

1. Ir a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Visual Merchandiser]** > **[!UICONTROL Visible Attributes for Category Rules]**, agregue categorías.
1. Vaya a Adobe Commerce > Administración > **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
   * Vaya a la [!UICONTROL Products in Category] sección.
   * Añadir un nuevo *[!UICONTROL Match products by rule]* con el atributo categories.

<u>Resultados esperados</u>:

La categoría se ha guardado correctamente.

<u>Resultados reales</u>:

* No puede guardar la categoría con la nueva regla y condición.
* *Error al guardar la categoría* se muestra el error.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
