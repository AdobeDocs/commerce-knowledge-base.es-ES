---
title: '"ACSD-56515: los administradores con permisos de nivel de sitio web no pueden editar [!UICONTROL Dynamic Block]'''
description: Aplique el parche ACSD-56515 para corregir el problema de Adobe Commerce en el que el administrador con permisos de nivel de sitio web no puede agregar ni editar el [!UICONTROL Dynamic Block].
feature: Roles/Permissions, Admin Workspace
role: Admin, Developer
exl-id: 5aa6b11e-b467-4076-ad36-162966cbf6df
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-56515: los administradores con permisos de nivel de sitio web no pueden editar [!UICONTROL Dynamic Block]

El parche ACSD-56515 corrige el problema en el que el administrador con permisos de nivel de sitio web no puede agregar ni editar el [!UICONTROL Dynamic Block]. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 está instalado. El ID del parche es ACSD-56515. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El administrador con permisos de nivel de sitio web no puede agregar ni editar el [!UICONTROL Dynamic Block].

<u>Pasos a seguir</u>:

1. Cree un sitio web secundario con tienda y vista de tienda.
1. Ir a **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]** y cree una función de usuario restringida al ámbito del sitio web secundario con todos los recursos disponibles.
1. Cree un usuario administrador con la función creada anteriormente.
1. Inicie sesión con el usuario administrador restringido y cree un [!UICONTROL Dynamic Block].

<u>Resultados esperados</u>:

El usuario administrador con restricciones en el sitio web puede crear un [!UICONTROL Dynamic Block].

<u>Resultados reales</u>:

Se obtiene el siguiente error: *Se necesitan más permisos para ver este elemento*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
