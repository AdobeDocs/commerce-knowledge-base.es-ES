---
title: "ACSD-53098: Los productos del catálogo compartido no se reflejan en el front-end"
description: Aplique el parche ACSD-53098 para corregir el problema de Adobe Commerce en el que los productos asignados a un catálogo compartido no se reflejan en el front-end al ejecutar un índice parcial.
feature: B2B, Catalog Management, Categories, Products
role: Admin, Developer
exl-id: 19c66a3a-04b2-48ee-aff3-ad2b592ff876
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-53098: los productos del catálogo compartido no se reflejan en el front-end

El parche ACSD-53098 corrige el problema de que los productos asignados a un catálogo compartido no se reflejan en el front-end al ejecutar un índice parcial. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.38 está instalado. El ID del parche es ACSD-53098. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los productos asignados a un catálogo compartido mediante API no aparecen en el front-end después de que el indexador parcial ejecute el trabajo cron, seguido del cron del consumidor.

<u>Pasos a seguir</u>:

1. Configuración de [!DNL RabbitMQ] como servicio de cola.
1. Cambiar indexadores a **[!UICONTROL Update on Schedule]** modo.
1. Cree un catálogo compartido y asígnelo a una empresa.
1. Cree un producto simple y asígnelo a una categoría. Ejecute el reindexado parcial:

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. Utilice la siguiente solicitud de API para asignar el producto creado al catálogo compartido.

   ```
   pub/rest/all/V1/sharedCatalog/<id>/assignProducts
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. Ejecute el siguiente cron para borrar las colas y ejecutar el reíndice parcial:

   `bin/magento cron:run --group=consumers`

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. Inicie sesión en el front-end como usuario de la compañía.
1. Compruebe la página de categoría de front-end.

<u>Resultados esperados</u>:

Los productos recién asignados aparecerán en el front-end.

<u>Resultados reales</u>:

Los productos recién asignados no aparecen en el front-end.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
