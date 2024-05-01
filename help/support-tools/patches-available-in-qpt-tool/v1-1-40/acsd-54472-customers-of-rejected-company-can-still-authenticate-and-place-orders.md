---
title: "ACSD-54472: los clientes de una empresa rechazada aún pueden autenticarse"
description: Aplique el parche ACSD-54472 para corregir el problema de Adobe Commerce en el que los clientes de una compañía rechazada aún pueden autenticarse y los clientes de una compañía bloqueada y rechazada pueden realizar pedidos.
feature: B2B
role: Admin, Developer
exl-id: 76fc4553-02b1-4563-91a9-0cda99fa4c7d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-54472: los clientes de una compañía rechazada aún pueden autenticarse

El parche ACSD-54472 corrige el problema en el que los clientes de una compañía rechazada aún pueden autenticarse, y los clientes de una compañía bloqueada y rechazada aún pueden realizar pedidos. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 está instalado. El ID del parche es ACSD-54472. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los clientes de una compañía rechazada aún pueden autenticarse, y los clientes de una compañía bloqueada y rechazada pueden realizar pedidos.

<u>Pasos a seguir</u>:

1. Cree una empresa.
1. Añadir productos al carro de compras mediante [!DNL GraphQL].
1. Cambie el estado de la empresa a *Bloqueado*.
1. Enviar un [!DNL GraphQL] solicitud para realizar el pedido y crear una oferta negociable.
1. Cambie el estado de la empresa a *Rechazado*.
1. Enviar un [!DNL GraphQL] para obtener el token de autorización de usuario de la empresa.
1. Definir el estado del cliente como *Inactivo*.
1. Enviar un [!DNL GraphQL] para obtener el token de autorización de usuario de la empresa.

<u>Resultados esperados</u>:

* El pedido y el presupuesto negociable no son colocados por el usuario del *Bloqueado* empresa.
* No se ha obtenido el token de autorización para el usuario del *Rechazado* empresa.
* No se ha obtenido el token de autorización para *Inactivo* cliente.

<u>Resultados reales</u>:

* El pedido y la cotización negociable son colocados por el usuario de la *Bloqueado* empresa.
* Se obtiene el token de autorización para el usuario del *Rechazado* empresa.
* Se obtiene el token de autorización para *Inactivo* cliente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
