---
title: "ACSD-51120: la caché de solicitudes de GET de GraphQL no se borra para las páginas de CMS que contienen bloques de CMS"
description: Aplique el parche ACSD-51120 para corregir el problema de Adobe Commerce en el que la caché de solicitudes de GET de GraphQL no se borra para páginas de CMS que contienen bloques de CMS.
exl-id: 22abba89-b697-45d7-972e-bf3233e5e9ec
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-51120: la caché de solicitudes de GET de GraphQL no se borra para las páginas de CMS que contienen bloques de CMS

El parche ACSD-51120 corrige el problema en el que la caché de solicitudes de GET de GraphQL no se borra para páginas de CMS que contienen bloques de CMS que se actualizan mediante una actualización de ensayo. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 está instalado. El ID del parche es ACSD-51120. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La caché de solicitudes de GET de GraphQL no se borra para las páginas de CMS que contienen bloques de CMS que se actualizan mediante una actualización de ensayo.

<u>Pasos a seguir</u>:

1. Cree un bloque CMS.
1. Incluya el bloque CMS en una página de CMS con la variable [!DNL Page Builder].
1. Recupere la página de CMS utilizando la consulta de GraphQL determinada mediante una solicitud de GET:

   ```GraphQL
   {
   cmsPage( identifier: "<CMS PAGE IDENTIFIER>") {
       content
       content_heading
       identifier
       meta_description
       meta_keywords
       meta_title
       page_layout
       title
       url_key
   }
   }
   ```

1. Asegúrese de que la respuesta de GraphQL se almacena en caché en [!DNL Varnish].
1. Cree una actualización programada para el bloque.
1. Espere a que se aplique la actualización programada y ejecute el trabajo cron para aplicar la actualización programada.
1. Recupere la página de CMS de nuevo con la consulta de GraphQL determinada mediante una solicitud de GET.

<u>Resultados esperados</u>:

La respuesta muestra el contenido actualizado.

<u>Resultados reales</u>:

La respuesta sigue mostrando el contenido antiguo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.


## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
