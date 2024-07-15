---
title: "ACSD-50815: la cantidad decimal para un producto simple no se puede utilizar para la nueva opción de producto agrupado"
description: Aplique el parche ACSD-50815 para corregir el problema de Adobe Commerce en el que la cantidad decimal de un producto simple no se puede utilizar para una nueva opción de producto agrupado.
feature: Products
role: Admin
exl-id: f4aa417c-b0eb-4a68-bf1e-fd86770cc72d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-50815: la cantidad decimal para un producto simple no se puede utilizar para la nueva opción de producto agrupado

El parche ACSD-50815 corrige el problema en el que la cantidad decimal de un producto simple no se puede utilizar para una nueva opción de producto agrupado. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35. El ID del parche es ACSD-50815. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La cantidad decimal de un producto simple no se puede utilizar para una nueva opción de producto agrupado.

<u>Pasos a seguir</u>:

1. Inicie sesión como administrador.
1. Cree un nuevo producto simple.
   * En la ventana **[!UICONTROL Advanced Inventory]**, establezca [!UICONTROL Qty Uses Decimal] = [!UICONTROL Yes].
   * Guarde el producto simple.
1. Cree un nuevo producto agrupado.
1. Añada cualquier opción.
1. Añada el producto simple a esta opción.
1. Establezca una cantidad decimal para el producto simple en la opción de producto agrupado. Por ejemplo, 1.5.

<u>Resultados esperados</u>:

Es posible establecer la cantidad decimal. No se muestran errores.

<u>Resultados reales</u>:

Error *Escriba un número válido en este campo*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
