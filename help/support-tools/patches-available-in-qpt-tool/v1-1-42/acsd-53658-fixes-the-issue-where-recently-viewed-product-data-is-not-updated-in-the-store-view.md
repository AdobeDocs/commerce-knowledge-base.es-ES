---
title: "ACSD-53658: **[!UICONTROL Recently Viewed Product]** datos no se actualizaron correctamente en la vista de la tienda"
description: Aplique el parche ACSD-53658 para solucionar el problema de Adobe Commerce donde los datos de **[!UICONTROL Recently Viewed Product]** no se actualizan correctamente en la vista de la tienda.
feature: CMS, Personalization
role: Admin, Developer
exl-id: 4086dcee-37e5-4393-9048-ce19a2d248e9
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-53658: **[!UICONTROL Recently Viewed Product]** datos no actualizados correctamente en la vista de almacén

La revisión ACSD-53658 corrige el problema en el cual los datos de **[!UICONTROL Recently Viewed Product]** no se actualizan correctamente en la vista de tienda. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42. El ID del parche es ACSD-53658. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los datos de **[!UICONTROL Recently Viewed Product]** no se actualizaron correctamente en la vista de la tienda.

<u>Pasos a seguir</u>:

1. Inicie sesión en el panel de administración.
1. Cree una segunda vista de tienda para el sitio web predeterminado.
1. Cree un producto sencillo.
1. Establece un nombre de producto diferente para la nueva vista de tienda.
1. Crear un widget **[!UICONTROL Recently Viewed Product]**.
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

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
