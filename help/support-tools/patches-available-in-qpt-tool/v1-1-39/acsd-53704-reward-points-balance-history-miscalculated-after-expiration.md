---
title: "ACSD-53704: El historial de saldo de puntos de recompensa se ha calculado incorrectamente tras la caducidad"
description: Aplique el parche ACSD-53704 para corregir el problema de Adobe Commerce en el que el historial de saldo de puntos de recompensa se calcula de forma incorrecta después de la fecha de caducidad de los puntos de recompensa.
feature: Rewards
role: Admin, Developer
exl-id: 5300cc22-0425-4467-b1e2-8bd799afb5fd
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-53704: el historial de saldo de puntos de recompensa se ha calculado mal tras la caducidad

El parche ACSD-53704 corrige el problema en el que el historial de saldo de puntos de recompensa se calcula de forma incorrecta después de la fecha de caducidad de los puntos de recompensa. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39 está instalado. El ID del parche es ACSD-53704. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El historial de saldo de puntos de recompensa se calcula de forma incorrecta después de la fecha de caducidad de los puntos de recompensa.

<u>Pasos a seguir</u>:

1. Cree un cliente en la tienda.
1. Agregue puntos de recompensa para el cliente con fechas de caducidad diferentes.
1. Compruebe la `magento_reward_history` y establezca la fecha de vencimiento del último registro de puntos de recompensa en una fecha pasada:

   ```
   UPDATE magento_reward_history SET expired_at_static = '2023-08-24 10:47:38' WHERE history_id = 3;
   ```

1. Compruebe la cuadrícula del historial de recompensas en **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit customer]** > **[!UICONTROL Reward points]** > **[!UICONTROL Reward Points History]** y **[!UICONTROL Reward Points Balance]**.

<u>Resultados esperados</u>:

El saldo de puntos de recompensa solo muestra los puntos no vencidos.

<u>Resultados reales</u>:

El saldo de puntos de recompensa refleja la cantidad que incluye los puntos vencidos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
