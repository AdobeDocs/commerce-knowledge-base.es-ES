---
title: "ACSD-46520: Estado de pedido incorrecto al reembolsarlo mediante créditos de la tienda"
description: Este artículo proporciona una solución para el problema en el que los usuarios obtienen un estado de pedido incorrecto cuando se les reembolsa mediante créditos de la tienda.
exl-id: 8464df22-0223-4ded-a15f-ce06eacdf77c
feature: Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-46520: Estado de pedido incorrecto al reembolsarlo mediante créditos de la tienda

El parche ACSD-46520 soluciona el problema en el que los usuarios obtienen un estado de pedido incorrecto cuando se les reembolsa mediante créditos de la tienda. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 está instalado. El ID del parche es ACSD-46520. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 y 2.4.2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.5

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios obtienen un estado de pedido incorrecto cuando se les reembolsa mediante créditos de la tienda.

<u>Pasos a seguir</u>:

1. Cree una cuenta de cliente en la tienda e inicie sesión.
1. Asigne créditos de tienda al cliente desde el administrador. Los créditos de la tienda deben cubrir todo el pedido.
1. Realice un pedido utilizando los créditos de la tienda.
1. Facturar el pedido.
1. Cree una nota de abono para devolver el importe total del pedido.
Seleccione el **[!UICONTROL Refund to store credit]** casilla de verificación
1. Compruebe el estado del pedido.

<u>Resultados esperados</u>:

El estado del pedido es *Cerrado*.

<u>Resultados reales</u>:

El estado del pedido es *Completar*, que no es el estado correcto.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* ADOBE COMMERCE o [!DNL Magento Open Source] local: [Parches de calidad > Herramientas > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía de la herramienta Parches de calidad.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía de la herramienta Parches de calidad.
