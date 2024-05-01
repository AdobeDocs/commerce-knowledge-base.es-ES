---
title: "ACSD-52133: la cuenta de cliente no se puede guardar después de una actualización"
description: Aplique el parche ACSD-52133 para corregir el problema de Adobe Commerce en el que una cuenta de cliente no se puede guardar después de una actualización.
feature: Customers, Upgrade
role: Admin
exl-id: 0db7c79e-10e1-4850-81b5-4812fb051941
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-52133: la cuenta de cliente no se puede guardar después de una actualización

El parche ACSD-52133 corrige el problema en el que una cuenta de cliente no se puede guardar después de una actualización. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.35 está instalado. El ID del parche es ACSD-52133. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La cuenta del cliente no se puede guardar después de una actualización.

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce versión 2.4.4.
1. Crear un cliente.
1. Actualice Adobe Commerce a 2.4.6 desde la versión anterior de 2.4.4, en la que ya se creó un cliente.
1. Establezca la clave de cifrado como se muestra a continuación en `env.php`:

   `d337b914e91ff703b1e94ba4156aadf0`

1. Configure los siguientes valores en la base de datos de cualquier cliente en `customer_entity` tabla:

   ```
   -> rp_token as incr4869
   -> rp_token_created_at as "2021-04-29 20:06:14"
   ```

1. Ir a **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Edite el cliente para el que se actualizaron los valores anteriores.
1. Haga clic en **[!UICONTROL Save Customer]** o **[!UICONTROL Save and Continue Edit]**

<u>Resultados esperados</u>:

El cliente se guarda correctamente sin errores.

<u>Resultados reales</u>:

* El registro de cliente no se ha guardado.
* El administrador recibe el siguiente mensaje de error: *Se ha producido un error al guardar el cliente.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
