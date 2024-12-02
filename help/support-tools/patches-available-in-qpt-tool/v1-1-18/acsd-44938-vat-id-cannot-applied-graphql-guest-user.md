---
title: 'ACSD-44938: VAT_ID no se puede aplicar en una solicitud de GraphQL para un usuario invitado'
description: El parche ACSD-44938 corrige el problema en el que el VAT_ID no se puede aplicar en una solicitud de GraphQL para un usuario invitado. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18. El ID del parche es ACSD-44938. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.
exl-id: 18b3dfa5-b666-491e-a067-526a53294f39
feature: Admin Workspace, GraphQL
role: Admin
source-git-commit: 77f41d6034f985794e5c5b89cc007a69858683b9
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-44938: VAT_ID no se puede aplicar en una solicitud de GraphQL para un usuario invitado

El parche ACSD-44938 corrige el problema en el que el VAT_ID no se puede aplicar en una solicitud de GraphQL para un usuario invitado. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18. El ID del parche es ACSD-44938. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

VAT_ID no se puede aplicar en una petición GraphQL para un usuario invitado.

<u>Pasos a seguir</u>:

1. Siga los pasos mencionados en el [tutorial de GraphQL](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) en nuestra documentación para desarrolladores para crear un carro de compras de invitado.
1. Intente aplicar VAT_ID al usuario invitado que utiliza GraphQL.

<u>Resultados esperados</u>:

VAT_ID se puede aplicar de la misma manera que para un cliente registrado. Consulte el artículo [createCustomerAddress mutation](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/create-address/) en nuestra documentación para desarrolladores.

<u>Resultados reales</u>:

VAT_ID no se puede aplicar a un usuario invitado que usa GraphQL.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en nuestra documentación para desarrolladores.
