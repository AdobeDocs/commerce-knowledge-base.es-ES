---
title: "ACSD-48212: la importación de productos asigna el producto a un origen incorrecto"
description: Aplique el parche ACSD-48212 para corregir el problema de Adobe Commerce donde la importación del producto asigna el producto al origen incorrecto.
exl-id: b3426f62-f73a-4b76-8e0e-544a9133720f
feature: Admin Workspace, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-48212: la importación de producto asigna el producto a un origen incorrecto

El parche ACSD-48212 corrige el problema en el que la importación del producto asigna el producto al origen incorrecto. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26. El ID del parche es ACSD-48212. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La importación de productos asigna el producto al origen incorrecto.

<u>Pasos a seguir</u>:

1. Crear un origen de inventario secundario.
1. Cree un producto con el origen de inventario predeterminado solamente.
1. Exporte el producto.
1. Ejecutar `bin/magento cron:run`.
1. Abra **[!UICONTROL Catalog]** > **[!UICONTROL Prdoucts]**.
1. Seleccione el producto en la cuadrícula.
1. Cancele la asignación de existencias mediante el menú *[!UICONTROL mass action]*.
1. Ejecutar `bin/magento cron:run`.
1. Asigne el origen secundario mediante el menú *[!UICONTROL mass action]*.
1. Ejecutar `bin/magento cron:run`.
1. Elimine el producto mediante el menú *[!UICONTROL mass action]*.
1. Ejecutar `bin/magento cron:run`.
1. Importe el producto utilizando el CSV exportado anteriormente.
1. Compruebe la asignación de origen.

<u>Resultados esperados</u>:

El producto solo está asignado al origen predeterminado.

<u>Resultados reales</u>:

El producto se asigna tanto al origen predeterminado como al secundario.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
