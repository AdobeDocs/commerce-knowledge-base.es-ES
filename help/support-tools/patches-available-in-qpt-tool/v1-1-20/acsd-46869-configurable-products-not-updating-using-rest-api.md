---
title: "ACSD-46869: Los productos configurables no se actualizan mediante la API de REST al cerrar la compra"
description: El parche ACSD-46869 corrige el problema en el que los productos configurables no se actualizan mediante la API de REST en el cierre de compra. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20. El ID del parche es ACSD-46869. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.
exl-id: d1bac489-f0f3-4b50-bc48-86c844230da7
feature: REST, Checkout, Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-46869: los productos configurables no se actualizan mediante la API de REST al cerrar la compra

El parche ACSD-46869 corrige el problema en el que los productos configurables no se actualizan mediante la API de REST al cerrar la compra. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 está instalado. El ID del parche es ACSD-46869. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.5

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL QPT] página de aterrizaje](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los productos configurables no se actualizan mediante la API de REST durante el cierre de compra.

<u>Pasos a seguir</u>:

1. Cree un producto configurable con atributos de color y tamaño.
1. Seleccionar **[!UICONTROL Options]** y añada el producto al carro de compras.
1. Ir a **[!UICONTROL Checkout]**, actualice el tamaño varias veces excepto para la cantidad y compruebe la solicitud y la respuesta.
1. Recibirá la siguiente respuesta cuando actualice el tamaño.

```REST API
{"extension_attributes":{"configurable_item_options":[
{"option_id":"960","option_value":25083},
{"option_id":"801","option_value":177}
]}}
```

<u>Resultados esperados</u>:

El valor se actualiza según los cambios.

<u>Resultados reales</u>:

`option_value` no se actualiza, por lo que cuando se realiza el pedido, tiene el valor de tamaño antiguo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tools] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía de la herramienta Parches de calidad.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en [!DNL QPT], consulte [Parches disponibles en [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía de la herramienta Parches de calidad.
