---
title: "ACSD-46581: El total de impuestos estimado no se actualiza después de seleccionar un país en el carro de compras"
description: Aplique el parche ACSD-46581 para resolver el problema de Adobe Commerce en el que la tasa impositiva no se actualiza después de cambiar el país en el carro de compras.
exl-id: 17334f7b-e5a2-4091-8196-eff80875c003
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-46581: el total de impuestos estimado no se actualiza después de seleccionar un país en el carro de compras

Este parche de ACSD-46581 resuelve el problema en el que la tasa impositiva no se actualiza después de cambiar el país en el carro de compras. Solo se actualiza después de seleccionar el método de envío. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 está instalado. El ID del parche es ACSD-46581. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.1-p1

**Compatible con las versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La tasa de impuestos no se actualiza después de cambiar de país en el carro de compras.

<u>Pasos a seguir</u>:

1. En Adobe Commerce Admin, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Tax Zone and Rates]**.
1. Crear un tipo impositivo nuevo para **[!UICONTROL Country]** = _Estados Unidos_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _8,25_.
1. Crear un tipo impositivo nuevo para **[!UICONTROL Country]** = _India_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _10_.
1. Cree una regla fiscal con ambos tipos impositivos para EE. UU. e India.
1. Ir a **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping Methods]** y habilitar más de un método de envío (_Tarifa plana_ y _Envío gratuito_ por ejemplo).
1. Cree un producto sencillo con **[!UICONTROL Taxable Goods]** clase de impuestos.
1. Añada el producto al carro de compras en la tienda.
1. Abra el carro de compras y compruebe la cantidad de impuestos.
1. Se aplica la configuración de impuestos predeterminada para Estados Unidos y el impuesto se calcula en función de una tasa del 8,25 %.
1. Cambia el país a la India.

<u>Resultados esperados</u>:

La cantidad de impuestos cambió al 10% cuando se cambió el país a la India.

<u>Resultados reales</u>:

La cantidad de impuestos sigue siendo la misma en la sección total del carro de compras.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
