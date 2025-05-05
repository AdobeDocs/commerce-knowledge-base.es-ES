---
title: "ACSD-56447: Añadir el mismo producto al carro de compras mediante la API de REST web paralela da como resultado dos elementos independientes en el carro de compras"
description: Aplique el parche ACSD-56447 para corregir el problema de Adobe Commerce, donde al agregar el mismo producto al carro de compras a través de solicitudes de API de REST web paralelas, se generan dos elementos independientes en el carro de compras.
feature: Shopping Cart, REST
role: Admin, Developer
exl-id: c63874be-a8a6-4143-adaa-ba3e9e107dd4
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-56447: Añadir el mismo producto al carro de compras mediante la API de REST web paralela resulta en dos elementos independientes en el carro de compras

El parche ACSD-56447 corrige el problema de que, al agregar el mismo producto al carro de compras mediante solicitudes de API de REST web paralelas, se generan dos elementos independientes en el carro de compras. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45. El ID del parche es ACSD-56447. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Añadir el mismo producto al carro de compras mediante solicitudes de API de REST web paralelas resulta en dos elementos independientes en el carro de compras.

<u>Pasos a seguir</u>:

1. Genere un token de cliente para realizar la solicitud de llamadas a la API de REST usando [!DNL Postman].
1. Cree un carro de compras para el cliente.
1. Utilice el token generado anteriormente para crear un carro de compras vacío para el cliente.
1. Use CURL para hacer dos solicitudes `AddProductsToCart` que se ejecuten en paralelo. Siga las instrucciones del [tutorial de procesamiento de pedidos](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/) de la documentación para desarrolladores.

<u>Resultados esperados</u>:

Los artículos con varias cantidades se muestran en una línea.

<u>Resultados reales</u>:

Los mismos SKU se muestran en elementos de varias líneas.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
