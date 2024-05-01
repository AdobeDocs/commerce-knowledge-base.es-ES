---
title: "ACSD-54026: Mensaje de error incorrecto para la solicitud de GraphQL updateCompanyRole"
description: Aplique el parche ACSD-54026 para corregir el problema de Adobe Commerce donde haya un mensaje de error incorrecto para una solicitud de GraphQL updateCompanyRole para un usuario no autorizado.
feature: Roles/Permissions
role: Admin, Developer
exl-id: c18a8815-975a-499d-a372-8635d89aa673
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-54026: Mensaje de error incorrecto para `updateCompanyRole` petición GraphQL

El parche ACSD-54026 corrige el problema en el que hay un mensaje de error incorrecto para una `updateCompanyRole` Solicitud de GraphQL para un usuario no autorizado. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.39 está instalado. El ID del parche es ACSD-54026. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Obtención de un mensaje de error incorrecto para una `updateCompanyRole` Solicitud de GraphQL para un usuario no autorizado.

<u>Pasos a seguir</u>:

1. Habilite la empresa B2B en la configuración.
1. Cree una empresa.
1. Enviar un `updateCompanyRole` Solicitud de GraphQL sin pasar un token de portador o con un token de portador no válido.
1. Observe el mensaje de error en la respuesta de GraphQL.

<u>Resultados esperados</u>:

Recibe el siguiente mensaje de error: *El cliente actual no está autorizado.*

<u>Resultados reales</u>:

Recibe el siguiente mensaje de error: *El cliente no es un usuario de la empresa.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
