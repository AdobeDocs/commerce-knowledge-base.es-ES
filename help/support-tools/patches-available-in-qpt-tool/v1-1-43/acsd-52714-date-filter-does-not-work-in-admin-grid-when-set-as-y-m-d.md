---
title: "ACSD-52714: El filtro de fecha no funciona en la cuadrícula de administración cuando se establece como d-m-a"
description: Aplique el parche ACSD-52714 para corregir el problema de Adobe Commerce en el que el filtro de fecha no funciona en la cuadrícula de administración cuando el formato de fecha se establece como d-m-a.
feature: Attributes
role: Admin, Developer
exl-id: b292ab2c-e12d-40df-a9ad-19f25fbde5a0
source-git-commit: 513cb47c054dbb907810bbdc3d20d2aca9d5e42b
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-52714: El filtro de fecha no funciona en la cuadrícula de administración cuando se establece como d-m-a

El parche ACSD-52714 corrige el problema de que el filtro de fecha no funciona en la cuadrícula de administración cuando el formato de fecha se establece como d-m-a. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 está instalado. El ID del parche es ACSD-52714. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El filtro de fecha no funciona en la cuadrícula de administración cuando el formato de fecha está establecido como d-m-a.

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce limpio.
1. Editar
   `/app/code/Magento/Customer/view/adminhtml/ui_component/customer_listing.xml`
archivo y añadir
   `<dateFormat>Y-MM-dd</dateFormat>`
hasta
   `<column name="created_at" class="Magento\Ui\Component\Listing\Columns\Date" component="Magento_Ui/js/grid/columns/date" sortOrder="100">`
en la etiqueta
   `<dataType>date</dataType>`

1. Vaciar la caché `bin/magento c:f`.
1. Inicie sesión en Admin y cree un nuevo cliente desde **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.

   * desde: fecha actual menos 1 día
   * hasta: fecha actual

1. Haga clic en **[!UICONTROL Apply Filters]**.

<u>Resultados esperados</u>:

El filtro de fecha de la cuadrícula funciona correctamente, independientemente de la configuración regional establecida.

<u>Resultados reales</u>:

Aparece el siguiente mensaje: *No hemos podido encontrar ningún registro*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
