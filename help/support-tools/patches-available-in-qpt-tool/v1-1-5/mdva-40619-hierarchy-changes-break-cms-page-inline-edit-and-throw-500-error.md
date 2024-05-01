---
title: "MDVA-40619: Los cambios de jerarquía rompen la edición en línea de la página de CMS y generan un error 500"
description: El parche MDVA-40619 resuelve el problema en el que los cambios en la jerarquía de páginas de CMS rompen la edición en línea de la página de CMS y lanzan "Error 500". Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5. El ID del parche es MDVA-40619. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: c003d845-1ba0-49c0-9f1a-a4b0ec00f30c
feature: CMS
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# MDVA-40619: Los cambios de jerarquía rompen la edición en línea de la página de CMS y generan un error 500

El parche MDVA-40619 resuelve el problema en el que los cambios en la jerarquía de páginas de CMS rompen la edición en línea de la página de CMS y lanzan &quot;Error 500&quot;. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 está instalado. El ID del parche es MDVA-40619. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los cambios de jerarquía de páginas de CMS rompen la edición en línea de la página de CMS y lanzan &quot;Error 500&quot;.

<u>Pasos a seguir</u>:

1. Vaya al Panel de administración > **Contenido** > **Jerarquía**.
1. Seleccione &quot;Vista de tienda predeterminada&quot;.
1. Desmarque &quot;Usar la jerarquía de nodos principal&quot;.
1. Seleccione la página manualmente y haga clic en **Guardar**.
1. A continuación, vaya a **Contenido** > **Páginas**.
1. Intente editar cualquier página de CMS desde la cuadrícula.
1. Clic **Guardar**.

<u>Resultados esperados</u>:

Página guardada correctamente.

<u>Resultados reales</u>:

Se obtiene el siguiente error:

*Un problema técnico con el servidor ha creado un error. Intenta de nuevo continuar lo que estabas haciendo. Si el problema persiste, inténtelo de nuevo más tarde.*

`Error: Call to a member function getData() on null in /magento2ee/app/code/Magento/VersionsCms/Controller/Adminhtml/Cms/Page/InlineEdit/Plugin.php:62`

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sección.
