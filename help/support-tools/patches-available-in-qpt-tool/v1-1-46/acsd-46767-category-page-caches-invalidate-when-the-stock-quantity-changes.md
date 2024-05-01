---
title: 'ACSD-46767: [!UICONTROL Category] las cachés de página invalidan cuando cambia la cantidad de stock'
description: Aplique el parche ACSD-46767 para solucionar el problema de Adobe Commerce donde la variable [!UICONTROL Category] las cachés de página invalidan cuando cambia la cantidad de stock, incluso si el producto sigue en stock.
feature: Cache, Products, Inventory
role: Admin, Developer
exl-id: 39811c03-8518-4975-a128-31537b4706c0
source-git-commit: b7e2ff7cd259963adb9a113eb8e94acdaa45ba1e
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-46767: [!UICONTROL Category] las cachés de página invalidan cuando cambia la cantidad de stock

El parche ACSD-46767 corrige el problema en el que la variable [!UICONTROL Category] las cachés de página invalidan cuando cambia la cantidad de stock, incluso si el producto sigue en stock. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 está instalado. El ID del parche es ACSD-46767. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

[!UICONTROL Category] las cachés de página invalidan cuando cambia la cantidad de stock.

<u>Pasos a seguir</u>:

1. Cree algunos productos y agréguelos a la misma categoría.
1. Abra el *[!UICONTROL Category]* en la tienda para asegurarse de que la página se almacena en caché.
1. Realizar el pedido con uno de los productos de la categoría *(la cantidad del producto se cambia, pero el producto sigue en stock)*.
1. Abra el [!UICONTROL Category] página de la tienda otra vez.

<u>Resultados reales</u>:

La página no se carga desde la caché. Se vuelve a generar.

<u>Resultados esperados</u>:

La página se carga desde la caché.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
