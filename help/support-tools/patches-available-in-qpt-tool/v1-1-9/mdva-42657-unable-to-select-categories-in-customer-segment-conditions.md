---
title: "MDVA-42657: No se pueden seleccionar categorías en las condiciones de segmentos del cliente"
description: El parche MDVA-42657 resuelve el problema en el que el usuario administrador no puede seleccionar categorías en las condiciones del segmento de cliente. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9. El ID del parche es MDVA-42657. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: 9c810dcd-b39b-4456-a362-5452ada4dc53
feature: Categories, Console, Customer Service
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-42657: No se pueden seleccionar categorías en las condiciones de segmentos del cliente

El parche MDVA-42657 resuelve el problema en el que el usuario administrador no puede seleccionar categorías en las condiciones del segmento de cliente. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9. El ID del parche es MDVA-42657. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario administrador no puede seleccionar categorías en las condiciones del segmento del cliente.

<u>Pasos a seguir</u>:

1. Vaya a **Clientes** > **Segmentos**.
1. Cree un nuevo segmento.
1. Vaya al segmento recién creado y haga clic en **Condiciones** en la navegación del lado izquierdo.
1. Haga clic en el signo más verde.
1. Seleccione Historial de productos en Productos.
1. Cambie &quot;visto&quot; por &quot;ordenado&quot;.
1. Cambie &quot;TODO&quot; por &quot;CUALQUIERA&quot;.
1. Haga clic en el signo más verde anidado y seleccione Categoría.
1. Haga clic en el signo **...** y, a continuación, haga clic en el icono del selector (a la izquierda de la marca de verificación).
1. Abra la consola de desarrollo del explorador.
1. Marque las casillas de verificación de una o varias categorías y observe el error de JavaScript producido en la consola.
1. Haga clic en el botón **Guardar**.
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

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/usage) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en nuestra documentación para desarrolladores.
