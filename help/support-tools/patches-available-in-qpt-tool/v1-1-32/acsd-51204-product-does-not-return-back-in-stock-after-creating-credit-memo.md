---
title: "ACSD-51204: El producto no vuelve a estar disponible después de crear la nota de crédito"
description: Aplique el parche ACSD-51204 para solucionar el problema de Adobe Commerce en el que el producto no vuelve a estar disponible después de crear la nota de crédito.
feature: Orders, Products, Returns
role: Admin
exl-id: 302033bc-2ca5-40d6-b692-24ae46b21c31
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-51204: El producto no vuelve a estar disponible después de crear la nota de crédito

El parche ACSD-51204 corrige el problema en el que el producto no vuelve a estar disponible después de crear la nota de crédito. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 está instalado. El ID del parche es ACSD-51204. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El producto agotado no vuelve a estar disponible después de crear la nota de crédito.

<u>Pasos a seguir</u>:

1. Instalar **[!UICONTROL Adobe Commerce]** y habilite la **[!UICONTROL Inventory Management Module]** con valor predeterminado *origen* y *existencias* solo.
1. Añadir un **[!UICONTROL new product]** con una cantidad de *10*.
1. Asigne el producto a **[!UICONTROL default stock]**.
1. En la Tienda, agrega el producto al carro y realiza un pedido de toda una cantidad disponible 10.
1. En el panel de administración, genere un *factura* y *envío* para el pedido.
1. Crear un **[!UICONTROL Credit Memo]** con el *volver a stock* casilla de verificación seleccionada para todos los elementos.
1. Compruebe el **[!UICONTROL Salable Quantity]** en el Administrador.

<u>Resultados esperados</u>:

La cantidad vendible del producto tiene que volver a *10*.

<u>Resultados reales</u>:

La cantidad vendible del producto se deja como *0*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) en el [!DNL Quality Patches Tool] guía.
