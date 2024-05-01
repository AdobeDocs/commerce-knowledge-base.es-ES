---
title: "ACSD-53414: Los usuarios administradores restringidos pueden ver páginas de CMS fuera de su ámbito de permisos"
description: Aplique el parche ACSD-53414 para corregir el problema de Adobe Commerce en el que un usuario administrador restringido puede ver páginas de CMS fuera de su ámbito de permisos.
feature: CMS
role: Admin, Developer
exl-id: f8540d52-a3bb-49bb-8868-7b1db03e571b
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-53414: los usuarios administradores restringidos pueden ver páginas de CMS fuera de su ámbito de permisos

El parche ACSD-53414 corrige el problema en el que un usuario administrador restringido puede ver páginas de CMS fuera de su ámbito de permisos. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 está instalado. El ID del parche es ACSD-53414. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios administradores restringidos pueden ver páginas de CMS más allá de su ámbito de permisos.

<u>Pasos a seguir</u>:

1. Cree un nuevo sitio web (sub_website), tienda (sub_store) y vista de tienda (sub_storeview).
1. Cree una función sub_expert, que permita el ámbito de sub_website y sub_store. Asigne solo los siguientes permisos: [!UICONTROL Dashboard] y [!UICONTROL Pages].
1. Cree un nuevo usuario administrador y asígnelo al rol sub_expert.
1. Asigne las siguientes páginas de CSM a la vista de subtienda y a la vista de tienda predeterminada.

   * [!UICONTROL 404 Not Found] > Vista de subtienda
   * [!UICONTROL 503 Service Unavailable] > Vista de tienda predeterminada

1. Inicie sesión en el administrador con el usuario administrador creado en el paso 3.
1. Compruebe la cuadrícula de la página de CMS.

<u>Resultados esperados</u>:

*[!UICONTROL 503 Service Unavailable]* La página no es visible para el administrador web.

<u>Resultados reales</u>:

*[!UICONTROL 503 Service Unavailable]* es visible para el administrador web.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
