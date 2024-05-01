---
title: "ACSD-51636: El administrador de la empresa no puede agregar nuevos usuarios desde la sección de cuenta de cliente"
description: Aplique el parche ACSD-51636 para solucionar el problema de Adobe Commerce en el que el administrador de la empresa no puede agregar nuevos usuarios desde la sección de cuenta de cliente a pesar de tener todas las funciones y permisos necesarios.
feature: Admin Workspace, B2B, Companies, Customer Service
role: Admin
exl-id: 78395584-e5d3-414e-859d-a68ce1af5af1
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-51636: el administrador de la empresa no puede agregar nuevos usuarios desde la sección de cuenta de cliente

El parche ACSD-51636 corrige el problema en el que el administrador de la empresa no puede agregar nuevos usuarios desde la sección de cuenta de cliente a pesar de tener todas las funciones y permisos necesarios. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34 está instalado. El ID del parche es ACSD-51636. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El administrador de la empresa no puede agregar nuevos usuarios desde la sección de cuenta de cliente a pesar de tener todas las funciones y permisos necesarios.

Requisitos previos:

* El módulo B2B está instalado.
* La funcionalidad de la empresa está habilitada.

<u>Pasos a seguir</u>:

1. Cree una nueva compañía.
1. Ir a **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Editar **[!UICONTROL Company Admin]** escriba a *Cliente*.
1. Inicie sesión como cliente.
1. Ir a **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** > **[!UICONTROL Add User]** y añadir detalles para el usuario y activarlo.
1. Guarde el nuevo usuario.

<u>Resultados esperados</u>

El usuario administrador puede agregar un nuevo usuario.

<u>Resultados reales</u>

* El usuario administrador recibe un mensaje de error: *Se ha producido un error*.
* El usuario administrador no puede crear un cliente nuevo.
* El registro contiene el siguiente error:

  ```PHP
      report.CRITICAL: Error: Call to a member function __toArray() on null in app/code/Magento/LoginAsCustomerLogging/Observer/LogSaveCustomerObserver.php:123
  ```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) en el [!DNL Quality Patches Tool] guía.
