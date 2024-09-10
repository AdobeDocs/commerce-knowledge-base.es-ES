---
title: "ACSD-48210: el atributo de ámbito específico de la vista de tienda anula los valores globales"
description: Aplique el parche ACSD-48210 para corregir el problema de Adobe Commerce de actualizar un atributo *[!UICONTROL Website Scope]* en una vista de almacén específica que anula los valores de atributo en el ámbito global.
feature: Products, Attributes
role: Admin, Developer
source-git-commit: 0fb14710d126aa4b4d6f5b6d0c70b190dcae81ae
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-48210: los atributos de ámbito específicos de vista de tienda anulan los valores globales

La revisión ACSD-48210 corrige el problema en el cual al actualizar un atributo *[!UICONTROL Website Scope]* dentro de una vista de almacén específica se anulan los valores de atributo en el ámbito global. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50. El ID del parche es ACSD-48210. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al actualizar un atributo *[!UICONTROL Website Scope]* en una vista de almacén específica, se anulan los valores de atributo en el ámbito global.

La importación de precios de productos con varias filas que comparten el mismo(a) `SKU` y `store_view_code` causó actualizaciones incorrectas de los precios en los ámbitos *[!UICONTROL All Store View]* y *[!UICONTROL Default Store]*. La modificación del atributo de ámbito del sitio web en una vista de almacén específica ya no anula el valor del atributo en el ámbito global.
<u>Pasos a seguir</u>:

1. Configure *[!UICONTROL Catalog Price Scope]* a *[!UICONTROL Website]*.
1. Cree un producto simple denominado *SP01* y establezca el precio en *$84.50*.
1. Importe el producto utilizando el siguiente CSV proporcionado a continuación:

   ```
   sku,store_view_code,price
   SP01,default,99.99
   SP01,default,86.59
   ```

1. Compruebe el precio del producto en los ámbitos *[!UICONTROL All Store View]* y *[!UICONTROL Default Store]*.

<u>Resultados esperados</u>:

* El primer valor no vacío se usa para el ámbito *[!UICONTROL Default Store]*.
* El ámbito *[!UICONTROL All Store View]* permanece sin cambios.

<u>Resultados reales</u>:

* El precio del ámbito *[!UICONTROL All Store View]* cambia a *$86,59*.
* El precio del ámbito *[!UICONTROL Default Store]* cambia a *$86,59*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].