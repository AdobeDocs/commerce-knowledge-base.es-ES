---
title: "ACSD-49389: listo para recibir correo electrónico enviado por API cuando no está listo para recibir"
description: Aplique el parche ACSD-49389 para solucionar el problema de Adobe Commerce donde la API envía un correo electrónico listo para recibir cuando el pedido no está listo para recibir.
exl-id: a1baae06-cf36-448b-bda4-aff1e5ca68db
feature: REST, Communications
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-49389: listo para recibir correo electrónico enviado por API cuando no está listo para recibir

El parche ACSD-49389 corrige el problema en el que la API envía un correo electrónico listo para recibir cuando el pedido no está listo para recibir. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 está instalado. El ID del parche es ACSD-49389. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [Página de aterrizaje de QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La API envía un correo electrónico listo para la recogida cuando el pedido no está listo para la recogida.

<u>Pasos a seguir</u>:

1. Activar *[!UICONTROL In-Store Delivery]* método.
1. Cree un origen de stock con la ubicación de recogida habilitada.
1. Cree nuevas existencias utilizando el sitio web principal con la fuente creada anteriormente.
1. Cree un producto que asigne el mismo origen.
1. Establecer cantidad de stock = 1.
1. Consulte el producto creado en el paso 4 con la *[!UICONTROL In-Store Delivery]* método de la tienda.
1. Cree una factura para el pedido.
1. Establezca la cantidad del producto en *0* y que quede fuera de stock.
1. Publique la siguiente solicitud de API:

```
{
    "orderIds": [
        1
    ]
}
```

<u>Resultados esperados</u>:

El correo electrónico listo para la recogida no se envía.

<u>Resultados reales</u>:

Devuelve API *El pedido no está listo para recoger*, pero listo para recibir correo electrónico se envía.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
