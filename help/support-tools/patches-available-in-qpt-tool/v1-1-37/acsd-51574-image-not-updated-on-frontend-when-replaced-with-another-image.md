---
title: "ACSD-51574: la imagen no se actualiza en el front-end cuando se sustituye por otra imagen"
description: Aplique el parche ACSD-51574 para corregir el problema de Adobe Commerce en el que la imagen no se actualiza en el front-end después de reemplazarla por otra imagen.
feature: Configuration
role: Admin
exl-id: a6f26126-71c3-43c2-bba4-60a914d7ec11
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-51574: la imagen no se actualiza en el front-end cuando se sustituye por otra imagen

El parche ACSD-51574 corrige el problema en el que la imagen no se actualiza en el front-end después de reemplazarla por otra imagen. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.37 está instalado. El ID del parche es ACSD-51574. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.7

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La imagen no se actualiza en el front-end después de reemplazarla por otra imagen.

<u>Pasos a seguir</u>:

1. Cree un producto con algunas imágenes.
1. Edite el producto y cargue una imagen con un nombre conocido (por ejemplo: *image.jpg*).
1. Guarde el producto.
1. Vuelva a editar el producto, elimine la versión antigua de la imagen y cargue la nueva versión de la imagen con el mismo nombre. **Asegúrese de que la nueva versión sea visiblemente diferente para ver el problema.**
1. Guarde el producto. Tanto el administrador como el front-end muestran las imágenes.
1. Vuelva a editar el producto y vuelva a cargar la misma imagen nueva (con el mismo nombre).
1. Guarde el producto y compruebe la página del producto en el front-end.

<u>Resultados esperados</u>:

La imagen cargada por segunda vez debe ser la nueva imagen, junto con el nombre cambiado de imagen.

<u>Resultados reales</u>:

La imagen cargada por segunda vez es la versión anterior de la imagen que se eliminó anteriormente, en lugar de la misma imagen nueva.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
