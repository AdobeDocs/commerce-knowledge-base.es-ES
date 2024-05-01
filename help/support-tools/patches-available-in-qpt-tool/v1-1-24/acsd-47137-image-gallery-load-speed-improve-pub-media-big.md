---
title: "ACSD-47137: mejorar la velocidad de carga de la galería de imágenes `pub/media` folder big"
description: Aplique el parche ACSD-47137 para mejorar la velocidad de carga de la galería de imágenes cuando la carpeta "pub/media" sea muy grande.
exl-id: 43268909-6845-4d1d-b6b8-4ae0ce40fd5e
feature: Cache, Catalog Management, Categories, Media
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-47137: mejorar la velocidad de carga de la galería de imágenes al `pub/media` carpeta grande

El parche ACSD-47137 mejora la velocidad de carga de la galería de imágenes cuando el `pub/media` La carpeta es muy grande. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 está instalado. El ID del parche es ACSD-47137. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con las versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La velocidad de carga de la galería de imágenes es lenta cuando la variable `pub/media` La carpeta es muy grande.

<u>Pasos a seguir</u>:

1. Vaya a Adobe Commerce > Administración > **[!UICONTROL STORES]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]** > **[!UICONTROL Enable Old Media Gallery]** hasta _No_.
1. Limpie la caché de configuración.
1. Cierre la sesión y vuelva a iniciarla como usuario administrador.
1. En la barra lateral de Administración, vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** y seleccione la categoría raíz.
1. Expanda el **[!UICONTROL Content]** y haga clic en **[!UICONTROL Select from Gallery]**.

Al cargar la página, Adobe Commerce envía `media_gallery/directories/gettree` solicitud para cargar el árbol de carpetas de medios.

<u>Resultados esperados</u>:

El `media_gallery/directories/gettree` La solicitud de solo debe cargar contenido de los directorios necesarios, que no sean crear un bucle de toda la lista de rutas desde el `pub/media/` carpeta.

<u>Resultados reales</u>:

El `media_gallery/directories/gettree` La solicitud tarda mucho tiempo en cargarse cuando el `pub/media/` tiene mucho contenido.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
