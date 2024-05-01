---
title: 'ACSD-47027: consulta lenta B2B [!UICONTROL CompanyRole] [!DNL GraphQL] update'
description: Aplique el parche ACSD-47027 para solucionar el problema de Adobe Commerce cuando haya una consulta B2B lenta [!UICONTROL CompanyRole] [!DNL GraphQL] actualizar.
exl-id: 478ae16b-7722-4469-8f8a-a38820e61ae4
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-47027: consulta lenta B2B [!UICONTROL CompanyRole] [!DNL GraphQL] actualizar

El parche ACSD-47027 resuelve el problema en el que la consulta lenta B2B [!UICONTROL CompanyRole] [!DNL GraphQL] la actualización no funciona según lo esperado. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 está instalado. El ID del parche es ACSD-47027. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con las versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La consulta lenta B2B [!UICONTROL CompanyRole] [!DNL GraphQL] la actualización no funciona según lo esperado.

<u>Requisitos previos</u>:

Instale el módulo B2B.

<u>Pasos a seguir</u>:

1. En Adobe Commerce Admin, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]** y establecer **[!UICONTROL Enable Company]** hasta _Sí_.
1. Vaya al front-end y cree una compañía.
1. Después de iniciar sesión como usuario de la empresa, vaya a **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]** y agregue una función nueva.
1. Activar [!UICONTROL dev] registro de consultas mediante `bin/magento dev:que:enab`.
1. Ahora envíe lo siguiente [!DNL GraphQL] solicitud (el id es el [!UICONTROL base64] función codificada (id):

   <pre><code>
   mutation {
   updateCompanyRole(
      input: {
         id: "Mg=="
         permissions: [
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        ]
      }
    ) {
      role {
         id

         name

         permissions {
         id

         text

         children {
            id

            text

            children {
               id

               text
             }
           }
         }
       }
     }
   }
   </code></pre>

1. Compruebe el registro de consultas.
1. Puede ver que se ejecuta la consulta anterior. Esta consulta se ejecuta en `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`.

<u>Resultados esperados</u>:

El `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` debe optimizarse para evitar cargar todos los datos disponibles en la **[!UICONTROL company_permissions]** Tabla de BD.

<u>Resultados reales</u>:

Adobe Commerce ejecuta una consulta sin ningún filtro. Cuando hay un gran número de registros, Adobe Commerce tarda mucho tiempo en preparar la recopilación de datos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores. 

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
