---
title: "ACSD-46520: Estado de pedido incorrecto al reembolsarlo mediante créditos de la tienda"
description: Este artículo proporciona una solución para el problema en el que los usuarios obtienen un estado de pedido incorrecto cuando se les reembolsa mediante créditos de la tienda.
exl-id: 8464df22-0223-4ded-a15f-ce06eacdf77c
feature: Orders, Returns
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-46520: Estado de pedido incorrecto al reembolsarlo mediante créditos de la tienda

El parche ACSD-46520 soluciona el problema en el que los usuarios obtienen un estado de pedido incorrecto cuando se les reembolsa mediante créditos de la tienda. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20. El ID del parche es ACSD-46520. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 y 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios obtienen un estado de pedido incorrecto cuando se les reembolsa mediante créditos de la tienda.

<u>Pasos a seguir</u>:

1. Cree una cuenta de cliente en la tienda e inicie sesión.
1. Asigne créditos de tienda al cliente desde el administrador. Los créditos de la tienda deben cubrir todo el pedido.
1. Realice un pedido utilizando los créditos de la tienda.
1. Facturar el pedido.
1. Cree una nota de abono para devolver el importe total del pedido.
Seleccione la casilla de verificación **[!UICONTROL Refund to store credit]**.
1. Compruebe el estado del pedido.

<u>Resultados esperados</u>:

El estado del pedido es *Cerrado*.

<u>Resultados reales</u>:

El estado del pedido es *Completo*, que no es el estado correcto.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o [!DNL Magento Open Source] de forma local: [Herramientas de parches de calidad > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía Herramienta de parches de calidad.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html?lang=es) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía de la herramienta Parches de calidad.
