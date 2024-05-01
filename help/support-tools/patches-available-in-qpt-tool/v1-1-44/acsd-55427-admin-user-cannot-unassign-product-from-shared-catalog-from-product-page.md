---
title: "ACSD-55427: un administrador no puede anular la asignación de un producto de **[!UICONTROL Product in Shared Catalogs]** en la página del producto"
description: Aplique el parche ACSD-55427 para corregir el problema de Adobe Commerce en el que no se puede anular la asignación de un producto de **[!UICONTROL Product in Shared Catalogs]**.
feature: Products, B2B
role: Admin, Developer
exl-id: 1e08def1-07f6-42e0-b600-9f0bfdd6477a
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-55427: un administrador no puede anular la asignación de un producto de **[!UICONTROL Product in Shared Catalogs]** en la página del producto

El parche de ACSD-55427 corrige el problema en el que no se puede anular la asignación de un producto de **[!UICONTROL Product in Shared Catalogs]** en la página del producto en el catálogo en Commerce Admin. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 está instalado. El ID del parche es ACSD-55427. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

No se puede anular la asignación de un producto de **[!UICONTROL Product in Shared Catalogs]** en la página del producto en el catálogo en Commerce Admin.

<u>Pasos a seguir</u>:

Requisitos previos: Adobe Commerce instalado con B2B y **[!UICONTROL Shared Catalogs]** activado.
1. Cree un producto.
1. Vaya al panel del catálogo compartido y abra el catálogo compartido predeterminado.
1. Asigne el producto al catálogo predeterminado y establezca un precio inferior al precio del producto.
1. Guarde el catálogo compartido.
1. Ejecute el [!UICONTROL CRON] para actualizar los consumidores/indexadores.
1. Abra el producto y elimínelo de debajo de **[!UICONTROL Product in Shared Catalogs]** sección.

<u>Resultados esperados</u>:

El producto debe retirarse de debajo de **[!UICONTROL Product in Shared Catalogs]** sección.

<u>Resultados reales</u>:

El producto sigue apareciendo en la **[!UICONTROL Product in Shared Catalogs]** sección.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
