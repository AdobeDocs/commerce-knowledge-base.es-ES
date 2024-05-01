---
title: "MDVA-42657: No se pueden seleccionar categorías en las condiciones de segmentos del cliente"
description: El parche MDVA-42657 resuelve el problema en el que el usuario administrador no puede seleccionar categorías en las condiciones del segmento de cliente. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9. El ID del parche es MDVA-42657. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: 9c810dcd-b39b-4456-a362-5452ada4dc53
feature: Categories, Console, Customer Service
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-42657: No se pueden seleccionar categorías en las condiciones de segmentos del cliente

El parche MDVA-42657 resuelve el problema en el que el usuario administrador no puede seleccionar categorías en las condiciones del segmento de cliente. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 está instalado. El ID del parche es MDVA-42657. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario administrador no puede seleccionar categorías en las condiciones del segmento del cliente.

<u>Pasos a seguir</u>:

1. Ir a **Clientes** > **Segmentos**.
1. Cree un nuevo segmento.
1. Vaya al segmento recién creado y haga clic en **Condiciones** en el panel de navegación izquierdo.
1. Haga clic en el signo más verde.
1. Seleccione Historial de productos en Productos.
1. Cambie &quot;visto&quot; por &quot;ordenado&quot;.
1. Cambie &quot;TODO&quot; por &quot;CUALQUIERA&quot;.
1. Haga clic en el signo más verde anidado y seleccione Categoría.
1. Haga clic en **...** y, a continuación, haga clic en el icono del selector (a la izquierda de la marca de verificación).
1. Abra la consola de desarrollo del explorador.
1. Marque las casillas de verificación de una o varias categorías y observe el error de JavaScript producido en la consola.
1. Haga clic en **Guardar** botón.
1. Vuelva a la condición y compruebe si se han guardado las categorías seleccionadas.

<u>Resultados esperados</u>:

Las categorías seleccionadas se guardan y seleccionan al ver o editar las condiciones del segmento.

<u>Resultados reales</u>:

Faltan las categorías seleccionadas y no se han guardado correctamente. Recibe el siguiente error en la consola:

```
category-checkbox-tree.js:249 Uncaught TypeError: Cannot set properties of undefined (setting 'value')
    at Ext.tree.TreePanel.Enhanced.<anonymous> (category-checkbox-tree.js:249)
    at Ext.util.Event.fire (ext-tree.js:29)
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
