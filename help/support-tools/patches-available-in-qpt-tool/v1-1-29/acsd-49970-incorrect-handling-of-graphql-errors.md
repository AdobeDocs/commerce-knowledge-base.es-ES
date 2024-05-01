---
title: "ACSD-49970: Gestión incorrecta de errores de GraphQL"
description: Aplique el parche ACSD-49970 para solucionar el problema de Adobe Commerce cuando haya un control incorrecto de los errores de GraphQL al [!UICONTROL New Relic Reporting] está activada.
exl-id: 70acade5-02a5-4769-86e2-5c566b2af709
feature: GraphQL, Observability
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-49970: Gestión incorrecta de errores de GraphQL

El parche ACSD-49970 corrige el problema en el que hay un control incorrecto de los errores de GraphQL cuando *[!UICONTROL New Relic Reporting]* está activada. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 está instalado. El ID del parche es ACSD-49970. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

`GraphQLOperationNames` no se gestiona correctamente si la clave `logDataHelper` contiene esta clave o no.

<u>Pasos a seguir</u>:

1. Ejecutar `bin/magento deploy:mode:set developer`.
1. Inicie sesión en Admin.
1. Activar **[!UICONTROL New Relic Integration]** de **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL New Relic Reporting]**
(Nota: Incluso si se muestra un error que indica que la variable [!DNL New Relic] extensión no está disponible, la configuración se ha guardado).
1. Ejecutar esto *GraphQL* mutación a `http://yourMagentoDomain/graphql` desde el *[!DNL Altair]* cliente o cualquier otro cliente o a través de cURL.

   ```GraphQL
   mutation {
       createEmptyCart
   }
   ```

   (Nota: Configure las variables **[!UICONTROL Header]** hasta [!UICONTROL Content-Currency:CA] antes de ejecutarlo).

   ```cURL
   curl --location 'http://yourMagentoDomain/graphql' \--header 'Content-Currency: CA' \--header 'Content-Type: application/json' \--header 'Cookie: PHPSESSID=b5147f63fe5014ea523f262946; private_content_version=8d53dfda210a6e9bc46f4e4a01ffd6c5' \--data '{"query":"mutation {\r\n  createEmptyCart\r\n}","variables":{}}'
   ```

<u>Resultados esperados</u>:

No hay ninguna *Excepción 500* en registros, `GraphQLOperationNames` La clave se está gestionando correctamente.

<u>Resultados reales</u>:

Hay un *Excepción 500* en registros, `GraphQLOperationNames` La clave no se gestiona correctamente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
