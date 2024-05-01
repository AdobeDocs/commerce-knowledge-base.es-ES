---
title: 'ACSD-54376: excepción en el carro de compras al eliminar el producto de [!UICONTROL shared catalog]'
description: Aplique el parche ACSD-54376 para solucionar el problema de Adobe Commerce cuando se produce una excepción en el carro de compras cuando se elimina un producto de [!UICONTROL shared catalog] después de agregarse al carro de compras.
feature: Shopping Cart, B2B
role: Admin, Developer
exl-id: a1e5c084-532f-49e8-ab87-6674b44218e8
source-git-commit: 1cc565d5888e5a380c04879d9aced2c19e92c2e5
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-54376: excepción en el carro de compras al eliminar el producto de [!UICONTROL shared catalog]

El parche ACSD-54376 corrige el problema en el que se produce una excepción en el carro de compras cuando se elimina un producto de [!UICONTROL shared catalog] después de agregarse al carro de compras. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 está instalado. El ID del parche es ACSD-54376. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se produce una excepción en el carro de compras cuando se elimina un producto de [!UICONTROL shared catalog] después de agregarse al carro de compras.

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce con B2B.
1. Activar [!UICONTROL shared catalog].
1. Crear un producto y asignarlo al predeterminado [!UICONTROL shared catalog].
1. Agregar un producto al carro de compras desde la tienda.
1. Elimine el producto del [!UICONTROL shared catalog].
1. Vaya a la página de cierre de compra mediante la lista desplegable de minicarro.

<u>Resultados esperados</u>:

Las excepciones se gestionan y no se muestran al usuario.

<u>Resultados reales</u>:

Se muestra una excepción no controlada en la página de cierre de compra.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
