---
title: "ACSD-49706: valor predeterminado guardado para el atributo de muestra visual cuando no se selecciona ningún valor"
description: Aplique el parche ACSD-49706 para corregir el problema de Adobe Commerce en el que se guarda un valor predeterminado para un atributo de muestra visual cuando no se selecciona ningún valor.
exl-id: fe6071df-f2a4-443a-acfa-67f3d253c5e4
feature: Admin Workspace, Attributes
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-49706: valor predeterminado guardado para el atributo de muestra visual cuando no se selecciona ningún valor

El parche ACSD-49706 corrige el problema en el que se guarda un valor predeterminado para un atributo de muestra visual cuando no se selecciona ningún valor. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 está instalado. El ID del parche es ACSD-49706. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se guarda un valor predeterminado para un atributo de muestra visual cuando no se selecciona ningún valor.

<u>Pasos a seguir</u>:

1. Ir a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**.
1. Clic **[!UICONTROL Add New Attribute]**.
1. Rellene los campos.

   * Por ejemplo, elija el tipo de entrada *[!UICONTROL Visual Swatch]* y agregue varias opciones (por ejemplo, *Rojo*, *Verde*). Asegúrese de elegir una de estas opciones como predeterminada.
   * Clic **[!UICONTROL Save Attribute]**.

1. Ir a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Edite el *[!UICONTROL Default]* conjunto de atributos.
1. Mover *[!UICONTROL New Attribute]* desde la columna *[!UICONTROL Unassigned Attributes]* a la *[!UICONTROL Product Details]* carpeta en la columna central.

   * Clic **[!UICONTROL Save]**.

1. Cree un nuevo producto con *[!UICONTROL Default]* conjunto de atributos.

   * Deje el *[!UICONTROL New Attribute]* vacíe y guárdelo.

1. Una vez guardado, aparece un valor en *[!UICONTROL New Attribute]*.

<u>Resultados esperados</u>:

No se ha asignado ningún valor a *[!UICONTROL New Attribute]* de forma predeterminada.

<u>Resultados reales</u>:

Al guardar un producto, se aplica un valor predeterminado al atributo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
