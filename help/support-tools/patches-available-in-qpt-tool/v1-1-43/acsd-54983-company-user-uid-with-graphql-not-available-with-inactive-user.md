---
title: "ACSD-54983: El UID de usuario de la empresa con GraphQL no está disponible con un usuario inactivo"
description: Aplique el parche ACSD-54983 para corregir el problema de Adobe Commerce en el que no es posible obtener el UID del usuario de la empresa con la solicitud de GraphQL cuando el estado del usuario se establece en inactivo.
feature: GraphQL
role: Admin, Developer
exl-id: 57e7b9ca-3421-4b50-86b4-abdf1b3d79d1
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-54983: el UID de usuario de la empresa con GraphQL no está disponible con usuarios inactivos

El parche ACSD-54983 corrige el problema en el que no es posible obtener el UID del usuario de la empresa con la solicitud de GraphQL cuando el estado del usuario se establece en inactivo. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 está instalado. El ID del parche es ACSD-54983. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

No se puede obtener el UID del usuario de la empresa con la solicitud de GraphQL cuando el estado del usuario se establece en inactivo.

<u>Pasos a seguir</u>:

1. Cree una compañía con un usuario administrador. Por ejemplo, company@test.com.
1. Crear un cliente nuevo.
1. Asigne el nuevo cliente a una compañía.
1. Obtenga una **[!UICONTROL company admin token]**.
1. Uso del **[!UICONTROL company admin token]**, recupere la estructura de la empresa. Consulte [Devolver la estructura de la empresa](https://developer.adobe.com/commerce/webapi/graphql/schema/b2b/company/queries/company/#return-the-company-structure) en nuestra documentación para desarrolladores.
1. La respuesta solo contiene *ACTIVO* clientes con sus ID.
1. Actualizar el usuario de la empresa a *INACTIVO*.
1. Recupere la estructura de la compañía de nuevo.

<u>Resultados esperados</u>:

Es posible obtener el UID del usuario de la empresa cuando el estado se establece en inactivo.

<u>Resultados reales</u>:

Los clientes inactivos no están en la lista. No se puede obtener el UID del usuario de la empresa cuando el estado se establece en inactivo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
