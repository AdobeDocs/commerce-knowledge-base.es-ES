---
title: "ACSD-54007: error _scope de clave de matriz no definida al importar datos del cliente"
description: Aplique el parche ACSD-54007 para solucionar el problema de Adobe Commerce donde se muestra un error Undefined array key _scope al importar datos del cliente.
feature: Data Import/Export
role: Admin, Developer
exl-id: b14a14fd-5021-460f-8ca9-c9845859df97
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-54007: error de _ámbito de clave de matriz no definido al importar datos de clientes

El parche ACSD-54007 corrige el problema en los casos en los que hay un *_Ámbito de clave de matriz no definido* error al importar los datos del cliente. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 está instalado. El ID del parche es ACSD-54007. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al importar datos de clientes, verá un *_Ámbito de clave de matriz no definido* error.

<u>Pasos a seguir</u>:

1. Vaya a Commerce > Administración > **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** >  **[!UICONTROL Import]**, configurado **[!UICONTROL Entity Type]** hasta **[!UICONTROL Stock Sources]** e importe el archivo csv de origen de stock (que contiene el código fuente, el SKU, la cantidad y el estado).
1. Elija Clientes y Direcciones (un solo archivo) e intente importar el archivo .csv, que contiene los detalles de dirección del cliente.

<u>Resultados esperados</u>:

No se obtienen errores.

<u>Resultados reales</u>:

Se obtiene el siguiente error:  *Advertencia: clave de matriz &quot;_scope&quot; sin definir en /var/www/html/vendor/magento/module-customer-import-export/Model/ResourceModel/Import/CustomerComposite/Data.php en la línea 84*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
