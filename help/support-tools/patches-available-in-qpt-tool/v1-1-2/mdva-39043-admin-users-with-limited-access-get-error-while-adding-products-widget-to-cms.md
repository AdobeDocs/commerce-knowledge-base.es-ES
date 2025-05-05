---
title: "MDVA-39043: Los usuarios administradores reciben un error al añadir un widget a la página de CMS"
description: El parche MDVA-39043 corrige el problema en el que los usuarios administradores con acceso limitado obtienen un error al añadir el widget "Productos" a la página de CMS. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.2. El ID del parche es MDVA-39043. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: 63057351-e972-4575-9bf0-e818f590b40a
feature: Admin Workspace, CMS, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-39043: Los usuarios administradores reciben un error al añadir un widget a la página de CMS

El parche MDVA-39043 corrige el problema en el que los usuarios administradores con acceso limitado obtienen un error al añadir el widget &quot;Productos&quot; a la página de CMS. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.2. El ID del parche es MDVA-39043. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.4 - 2.4.3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios administradores con acceso limitado obtienen un error al añadir el widget &quot;Productos&quot; a la página de CMS.

<u>Pasos a seguir</u>:

1. Inicie sesión en el servidor utilizando el administrador con acceso solo para editar contenido.
1. Vaya a **Contenido** > **Páginas**.
1. Abra cualquier página para editarla.
1. Edite el contenido con **Page Builder**.
1. Agregar el widget **Producto** de la sección **Agregar contenido**.
1. Haga clic en **Configurar** en el widget **Producto**.

<u>Resultados esperados</u>:

No se muestra ningún error.

<u>Resultados reales</u>:

Se recibe el siguiente mensaje de error:

`*A technical problem with the server created an error. Try again to continue what you were doing. If the problem persists, try again later.*`

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/usage) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en nuestra documentación para desarrolladores.
