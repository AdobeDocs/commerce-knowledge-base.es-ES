---
title: '''ACSD-53658: **[!UICONTROL Recently Viewed Product]** datos no se han actualizado correctamente en la vista de tienda"'
description: Aplique el parche ACSD-53658 para solucionar el problema de Adobe Commerce donde **[!UICONTROL Recently Viewed Product]** datos no se actualizan correctamente en la vista de la tienda.
feature: CMS, Personalization
role: Admin, Developer
exl-id: 4086dcee-37e5-4393-9048-ce19a2d248e9
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-53658: **[!UICONTROL Recently Viewed Product]** los datos no se actualizan correctamente en la vista de tienda

El parche ACSD-53658 corrige el problema donde **[!UICONTROL Recently Viewed Product]** los datos de no se actualizan correctamente en la vista de tienda. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 está instalado. El ID del parche es ACSD-53658. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El **[!UICONTROL Recently Viewed Product]** los datos de no se actualizan correctamente en la vista de tienda.

<u>Pasos a seguir</u>:

1. Inicie sesión en el panel de administración.
1. Cree una segunda vista de tienda para el sitio web predeterminado.
1. Cree un producto sencillo.
1. Establece un nombre de producto diferente para la nueva vista de tienda.
1. Crear un **[!UICONTROL Recently Viewed Product]** widget.
1. Configure este widget para que se muestre en la página de inicio.
1. Abra la página del producto en la Tienda desde la vista predeterminada de la tienda.
1. Abra la página Inicio.
1. Con el conmutador de tiendas, cambie a la vista de la segunda tienda.

<u>Resultados esperados</u>:

El nombre del producto se actualiza en el widget.

<u>Resultados reales</u>:

El nombre del producto no se actualiza en el widget.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
