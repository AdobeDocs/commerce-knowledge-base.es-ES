---
title: "ACSD-56858: discrepancia en los permisos de funciones en el administrador de la empresa B2B"
description: Aplique el parche ACSD-56858 para corregir el problema de Adobe Commerce en el que los permisos de funciones se muestran incorrectamente para un administrador de empresa restringido en el entorno B2B.
feature: Companies, B2B, Roles/Permissions
role: Admin, Developer
exl-id: d446f815-78bf-42ec-bc2b-a5934b15b416
source-git-commit: 4bf5deb1115705560acc8410441219943329c1a4
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-56858: discrepancia en los permisos de funciones en el administrador de la empresa B2B

El parche ACSD-56858 corrige el problema de que los permisos de funciones se muestran incorrectamente para un administrador de empresa restringido en el entorno B2B. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.47 está instalado. El ID del parche es ACSD-56858. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los permisos de funciones para un administrador de empresa restringido en el entorno B2B se muestran de forma incorrecta.

<u>Pasos a seguir</u>:

1. Comience por configurar una empresa y agregar un administrador de empresa y usuarios de empresa.
1. Inicie sesión como administrador de la empresa en la tienda y cree varias funciones para distintos usuarios.
1. Asigne estas funciones según sea necesario, como limitar el acceso para algunas tareas y permitir el acceso completo para otras.
1. Asigne estas funciones con acceso completo a un usuario que no sea el administrador de la empresa.
1. Inicie sesión en un usuario que no sea administrador de la empresa, por ejemplo, un administrador de la empresa.
1. Vaya a **[!UICONTROL Roles and permission]** y editar la función.
1. Observe que los permisos mostrados no coinciden con los permisos establecidos en la base de datos de la empresa para ese ID de rol.

<u>Resultados esperados</u>:

Los roles y los permisos aparecen correctamente para el usuario que no es administrador de la empresa.

<u>Resultados reales</u>:

Los roles no aparecen correctamente para el usuario administrador que no es de la empresa según los registros de la base de datos en la tabla de permisos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
