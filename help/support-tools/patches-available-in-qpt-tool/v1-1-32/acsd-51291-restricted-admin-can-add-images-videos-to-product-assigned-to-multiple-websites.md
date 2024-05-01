---
title: "ACSD-51291: el administrador restringido puede agregar imágenes/vídeos al producto asignado a varios sitios web"
description: Aplique el parche ACSD-51291 para solucionar el problema de Adobe Commerce, donde los administradores restringidos con acceso a un sitio web pueden agregar imágenes/vídeos a un producto asignado a varios sitios web.
feature: Admin Workspace, Products, Page Content
role: Admin
exl-id: d3cf5009-6b80-4841-95c3-75bb15c9c0a4
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# ACSD-51291: un administrador restringido puede añadir imágenes/vídeos al producto asignado a varios sitios web

El parche ACSD-51291 corrige el problema en el que un administrador restringido con acceso a un sitio web puede agregar imágenes/vídeos a un producto asignado a varios sitios web. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 está instalado. El ID del parche es ACSD-51291. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.4-p3, 2.4.5 - 2.4.5-p2

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Un administrador restringido con acceso a un sitio web puede agregar imágenes o vídeos a un producto asignado a varios sitios web.

<u>Pasos a seguir</u>

1. Inicie sesión como administrador.
1. Cree un segundo sitio web, tienda y vista de tienda.
1. Cree una segunda función de administrador con recursos solo para la segunda vista del sitio web, la tienda y la tienda.
1. Cree un segundo administrador y asígnelo al nuevo rol de administrador restringido.
1. Cree un nuevo producto y asígnelo a los sitios web predeterminados y a los nuevos.
1. Cierre la sesión del perfil de administrador principal.
1. Inicie sesión como el nuevo administrador restringido.
1. Edite el producto creado, que se ha asignado a ambos sitios web.
1. Abra el **[!UICONTROL Images and Videos]** pestaña.

<u>Resultados esperados</u>:

* Se muestra el siguiente mensaje:

  *El administrador restringido solo puede realizar acciones con imágenes o vídeos si tiene derechos sobre todos los sitios web a los que está asignado el producto.*

* El **[!UICONTROL Add Video]** El botón no está activo.

<u>Resultados reales</u>:

El administrador restringido puede añadir imágenes y vídeos incluso cuando el producto está asignado a un sitio web al que no tiene acceso.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
