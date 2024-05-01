---
title: '''ACSD-52786: Regla de catálogo *[!UICONTROL SKU is]* se aplica a todos los productos que comienzan con el SKU'
description: Aplique el parche ACSD-52786 para corregir el problema de Adobe Commerce donde la condición de regla de catálogo *[!UICONTROL SKU is]* se aplica a todos los productos que comienzan con el SKU determinado.
feature: Price Rules
role: Admin
exl-id: af373b6c-5944-412b-a544-cc6fc3f209d3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-52786: Regla de catálogo &quot;*[!UICONTROL SKU is]*&quot; se aplica a todos los productos que comienzan con el SKU

El parche ACSD-52786 corrige el problema en el que la condición de regla de catálogo *[!UICONTROL SKU is]* se aplica a todos los productos que comienzan con el SKU determinado. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.35 está instalado. El ID del parche es ACSD-52786. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Condición de regla de catálogo *[!UICONTROL SKU is]* se aplica a todos los productos que comienzan con el SKU determinado.

<u>Pasos a seguir</u>:

1. Cree dos productos, uno con el SKU &quot;24&quot; y otro con el SKU &quot;24-MB01&quot;.
1. Vaya a **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**.
1. Aplique la siguiente condición:
   * *[!UICONTROL If ** TODO **Algunas de estas condiciones son** VERDADERO **]*: *[!UICONTROL SKU is 24]*
1. Defina cualquier importe de descuento en las acciones.
1. Clic **[!UICONTROL Save and Apply]**.
1. Vaciar caché.
1. Vaya a la tienda y compruebe el precio de 24 MB01.

<u>Resultados esperados</u>:

La regla de catálogo solo se aplica a un único producto con SKU igual a 24.

<u>Resultados reales</u>:

Condición de regla de catálogo *[!UICONTROL SKU is]* se aplica a todos los productos que comienzan con el SKU determinado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
