---
title: '"ACSD-51739: Error al solicitar "structure_id" en la solicitud de GraphQL de "CompanyTeam"'
description: Aplique el parche ACSD-51739 para solucionar el problema de Adobe Commerce donde se devuelve un error cuando se solicita structure_id en una solicitud de GraphQL de CompanyTeam.
exl-id: 31c085e0-c8be-4709-9620-80ff360dca9a
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-51739: Error al solicitar `structure_id` in `CompanyTeam` petición GraphQL

El parche ACSD-51739 corrige el problema en el que se devuelve un error cuando la variable `structure_id` se solicita en un `CompanyTeam` petición GraphQL. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34 está instalado. El ID del parche es ACSD-51739. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se devuelve un error cuando la variable `structure_id` se solicita en un `CompanyTeam` petición GraphQL.

<u>Pasos a seguir</u>

1. Ir a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** y establezca *[!UICONTROL Enable Company]* hasta *Sí*.
1. Cree una empresa junto con un usuario administrador de la empresa.
1. Crear un cliente nuevo (*cliente1*) y asigne la empresa (creada anteriormente) a este cliente.
1. En el front-end, inicie sesión como el usuario administrador de la empresa.
1. Cree un equipo de empresa y asigne *cliente1* al equipo mediante arrastrar y soltar.
1. Ejecute la siguiente consulta de GraphQl de la empresa, que incluye `CompanyTeam` con `structure_id`:

   ```GraphQL
   query{
       company {
           id
           name
           structure {
               items {
               id
               parent_id
               entity {
                   __typename
                   ... on Customer {
                       firstname
                       lastname
                       email
                       structure_id
                   }
                   ... on CompanyTeam {
                       id
                       name
                       structure_id
                   }
               }
       }
   }
   }
   }
   ```

1. Compruebe la respuesta de GraphQL.

<u>Resultados esperados</u>:

No se devuelve ningún error y todos los datos solicitados están presentes en la respuesta de GraphQL.

<u>Resultados reales</u>:

* La respuesta contiene un *Error interno del servidor*.
* `var/log/exception.log` contiene:

  ```
  report.ERROR: Cannot return null for non-nullable field "CompanyTeam.structure_id"
  ```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
