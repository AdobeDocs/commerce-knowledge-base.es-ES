---
title: "ACSD-47179: la eliminación masiva de críticas de productos no funciona cuando se inicia sesión como función de usuario limitada"
description: Aplique el parche ACSD-47179 para corregir el problema de Adobe Commerce en el que la eliminación masiva de revisiones de productos no funciona cuando se inicia sesión como una función de usuario limitada.
exl-id: 85d7ce63-7dd6-4df4-b314-278d18e69fbb
feature: Marketing Tools, Products, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-47179: la eliminación masiva de críticas de productos no funciona cuando se inicia sesión como una función de usuario limitada

El parche ACSD-47179 corrige el problema en el que la eliminación masiva de revisiones de productos no funciona cuando se inicia sesión como una función de usuario limitada. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 está instalado. El ID del parche es ACSD-47179. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La eliminación masiva de críticas de productos no funciona cuando se inicia sesión como una función de usuario limitada.

<u>Pasos a seguir</u>:

1. Crear un sitio web secundario.
1. Cree una función de usuario restringida al sitio web secundario con pleno permiso para las siguientes secciones:
   * Catálogo
   * Cliente
   * Marketing
1. Cree un producto y asígnelo al sitio web secundario.
1. Agregue dos críticas al producto desde el front-end.
1. Inicie sesión en [!DNL Commerce] Administrador con el usuario administrador restringido que se acaba de crear.
1. Intente eliminar de forma masiva las revisiones pendientes.

<u>Resultados esperados</u>:

Un administrador con permisos suficientes puede eliminar de forma masiva las revisiones pendientes.

<u>Resultados reales</u>:

Se obtiene el siguiente error: _Se ha producido un error. Excepción generada en support_report.log_

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
