---
title: '"ACSD-57074: *Sí/No* el atributo personalizado con el prefijo "price_*" en el atributo "attribute_code" no funciona con la indexación"'
description: Aplique el parche ACSD-57074 para solucionar el problema de Adobe Commerce donde el atributo personalizado *Yes/No* con el prefijo "price_* en el atributo "attribute_code" no funciona con la indexación.
feature: Products, Categories, Catalog Management
role: Admin, Developer
exl-id: c620722f-a66d-4cae-9614-becec589a78c
source-git-commit: 4197f2a8f3d4775d3459b17bd92fa51a54ff9607
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-57074: *Sí/No* atributo personalizado con `price_*` prefijo en `attribute_code` el atributo no funciona con la indexación

El parche ACSD-57074 corrige el problema en el que la variable *Sí/No* atributo personalizado con `price_*` prefijo en `attribute_code` El atributo no funciona con la indexación. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.47 está instalado. El ID del parche es ACSD-57074. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El *Sí/No* atributo personalizado con `price_*` prefijo en `attribute_code` El atributo no funciona con la indexación.

<u>Pasos a seguir</u>:

1. Cree un atributo de producto personalizado con las siguientes opciones:
   * *[!UICONTROL Catalog Input Type]*: *Sí/No*
   * *[!UICONTROL Scope]*: *StoreView*
   * *[!UICONTROL Use in Search]*: *Sí*
1. Asigne el atributo al conjunto de atributos predeterminado.
1. Cree un producto con el atributo que hemos creado.
1. Asigne el producto que hemos creado a una categoría.
1. Ejecutar reindexación completa.

<u>Resultados esperados</u>:

El producto se muestra en la categoría asignada.

<u>Resultados reales</u>:

El producto no aparece en la página de categoría principal.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
