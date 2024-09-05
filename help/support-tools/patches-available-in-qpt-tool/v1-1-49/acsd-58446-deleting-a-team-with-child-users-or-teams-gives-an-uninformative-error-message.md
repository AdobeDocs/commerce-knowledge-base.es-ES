---
title: "ACSD-58446: La eliminación de un equipo con usuarios o equipos secundarios a través de GraphQL da un mensaje de error no informativo"
description: Aplique el parche ACSD-58446 para corregir el problema de Adobe Commerce en el que al eliminar un equipo con usuarios o equipos secundarios a través de GraphQL se devuelve un mensaje de error no informativo incoherente con la interfaz de usuario.
feature: Product, GraphQL, Company
role: Admin, Developer
source-git-commit: ab290f7c5b052aa220b3ef003febd9afc1cfdf00
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-58446: La eliminación de un equipo con usuarios o equipos secundarios a través de GraphQL da un mensaje de error no informativo

El parche de ACSD-58446 corrige el problema de Adobe Commerce, donde al eliminar un equipo con usuarios o equipos secundarios a través de GraphQL, se devuelve un mensaje de error no informativo incoherente con la interfaz de usuario. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49. El ID del parche es ACSD-58446. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce B2B 1.5.1

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p4

**Compatible con Adobe Commerce y versiones de Magento Open Source:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p7

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al eliminar un equipo con usuarios o equipos secundarios a través de GraphQL, se devuelve un mensaje de error no informativo incoherente con la interfaz de usuario.

## Condiciones previas:

Módulos B2B instalados.

<u>Pasos a seguir</u>:

1. Habilite la funcionalidad *[!UICONTROL Company]*.
1. Cree una nueva cuenta de compañía.
1. Inicie sesión en **[!UICONTROL Admin]** y active la cuenta de la compañía.
1. Compruebe el correo electrónico y establezca una contraseña para la nueva cuenta de empresa.
1. Cree un nuevo equipo para la compañía.
1. Inicie sesión como **[!UICONTROL company user]** en el front-end y agregue **[!UICONTROL new user]** para el equipo creado.
1. Inicie sesión en **[!UICONTROL Admin]**, deshabilite el usuario de la compañía y establezca *[!UICONTROL Customer Active]* = *No*
1. Asegúrese de eliminar el equipo creado mediante GraphQL.

   ```
   mutation {
     deleteCompanyTeam(
       id: "MQ=="
     ) {
       success
     }
   }
   ```

<u>Resultados esperados</u>:

Se devuelve un mensaje de error informativo coherente con la interfaz de usuario.

<u>Resultados reales</u>:

Se devuelve un mensaje de error interno genérico del servidor.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].