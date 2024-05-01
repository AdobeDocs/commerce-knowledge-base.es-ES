---
title: "ACSD-56546: Los productos configurables y agrupados se muestran como agotados en la tienda"
description: Aplique el parche ACSD-56546 para solucionar el problema de Adobe Commerce en el que los productos configurables y del paquete se muestran como agotados en la tienda cuando la etiqueta *[!UICONTROL Display Out of Stock Products]* la opción de configuración está desactivada.
feature: Storefront, Products
role: Admin, Developer
exl-id: 488e2c69-442f-45e1-aa8f-71d9c0a93950
source-git-commit: 031d5cad6727bac61c88f21fa7c84e0d2a6df331
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-56546: los productos configurables y agrupados se muestran como agotados en la tienda

El parche ACSD-56546 corrige el problema en el que los productos configurables y del paquete se muestran como agotados en la tienda. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 está instalado. El ID del parche es ACSD-56546. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los productos configurables y agrupados se muestran como agotados en la tienda cuando *[!UICONTROL Display Out of Stock Products]* La opción está desactivada.

<u>Pasos a seguir</u>:

1. Configure las variables **[!UICONTROL Display Out of Stock Products]** opción para *No*.
1. Cree un sitio web, una tienda y una vista de tienda.
1. Cree un origen y un inventario y, a continuación, asígnelo al segundo sitio web.
1. Crear un *producto configurable* con dos productos secundarios. Asigne los productos secundarios a ambos orígenes y a ambos sitios web.
1. Actualizar el primer producto secundario que se tiene *qty=0* en ambas fuentes.
1. Actualice el segundo producto secundario y desactívelo en el segundo sitio web.
1. Realice una reindexación completa.
1. Compruebe la categoría que contiene el producto configurable en el segundo sitio web.

<u>Resultados esperados</u>:

Los productos configurables que no tienen existencias no son visibles en la tienda.

<u>Resultados reales</u>:

Los productos configurables que no tienen existencias son visibles en la tienda incluso cuando el *[!UICONTROL Display Out of Stock Products]* La opción está desactivada.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
