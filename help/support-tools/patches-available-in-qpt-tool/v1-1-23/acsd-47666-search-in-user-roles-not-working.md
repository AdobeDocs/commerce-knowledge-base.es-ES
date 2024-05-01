---
title: 'ACSD-47666: buscar en [!UICONTROL User Roles] no funciona'
description: Aplique el parche ACSD-47666 para corregir el problema de Adobe Commerce en el que el filtro funciona [!UICONTROL User Roles] no funciona como se esperaba.
exl-id: c1b6d3ab-e132-4b09-8692-2b82f9ca6864
feature: Roles/Permissions, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# ACSD-47666: buscar en **[!UICONTROL User Roles]** no funciona

El parche ACSD-47666 resuelve el problema en el que la búsqueda en **[!UICONTROL User Roles]** no funciona. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 está instalado. El ID del parche es ACSD-47666. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La función de filtro está activada **[!UICONTROL User Roles]** no funciona como se esperaba.

<u>Pasos a seguir</u>:

1. Inicie sesión en Adobe Commerce Admin > **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]**.
1. Abra cualquier función existente de la lista.
1. Abra el **[!UICONTROL Role Users]** pestaña.
1. Escriba cualquier consulta en una columna.
1. Pulse Intro.

<u>Resultados esperados</u>:

El **[!UICONTROL User Roles]** la función de filtro debe filtrar los resultados en función de la consulta.

<u>Resultados reales</u>:

Carga infinita con error de consola _(índice):9 TypeError no capturado: no se pueden leer las propiedades de null (leyendo &#39;down&#39;)_.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores. 

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
