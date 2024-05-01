---
title: '''ACSD-47336: [!UICONTROL Something went wrong] error al descartar las notificaciones en "Administración de Adobe Commerce"'
description: Aplique el parche ACSD-47336 para solucionar el problema de Adobe Commerce donde el usuario ve [!UICONTROL Something went wrong] error al descartar notificaciones en [!DNL Commerce] Administrador.
exl-id: 7561f055-ce04-4a49-8c58-271c24420a60
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-47336: _[!UICONTROL Something went wrong]_error al descartar las notificaciones en el administrador de Adobe Commerce

El parche ACSD-47336 corrige el problema en el que el usuario ve el _[!UICONTROL Something went wrong]_error al descartar notificaciones en [!DNL Commerce] Administrador. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 está instalado. El ID del parche es ACSD-47336. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación): 2.4.5

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación): 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario ve _[!UICONTROL Something went wrong]_error al descartar notificaciones en [!DNL Commerce] Administrador.

<u>Pasos a seguir</u>:

1. Realice una operación por lotes (por ejemplo, una actualización por lotes de los atributos de producto de la cuadrícula de productos).
1. Complete la operación (por ejemplo, ejecute `bin/magento queue:consumer:start product_action_attribute.update`).
1. Actualice la [!DNL Commerce] En la página de administración, expanda la sección de notificaciones de administración y haga clic en **[!UICONTROL Dismiss All Completed Tasks]** vínculo.

<u>Resultados esperados</u>:

El _[!UICONTROL Something went wrong]_no debería mostrarse ningún error al borrar las tareas completadas.

<u>Resultados reales</u>:

El _[!UICONTROL Something went wrong]_se muestra el error.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
