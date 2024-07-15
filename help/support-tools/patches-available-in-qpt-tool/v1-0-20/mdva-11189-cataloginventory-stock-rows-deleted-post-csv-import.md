---
title: "MDVA-11189: filas cataloginventory_stock eliminadas tras la importación de CSV"
description: El parche de MDVA-11189 Adobe Commerce corrige el problema cuando, después de importar un archivo .csv para actualizar las existencias del producto, se eliminan las filas de la tabla cataloginventory_stock. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. El ID del parche es MDVA-1189. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.3.5.
exl-id: 84e1979c-826c-4c01-b0c7-8054bb4b23f0
feature: Catalog Management, Data Import/Export, Inventory, Orders
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# MDVA-11189: filas cataloginventory_stock eliminadas tras la importación de CSV

El parche de MDVA-11189 Adobe Commerce corrige el problema cuando, después de importar un archivo .csv para actualizar las existencias del producto, se eliminan las filas de la tabla `cataloginventory_stock`. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. El ID del parche es MDVA-1189. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.3.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:** Adobe Commerce en la infraestructura en la nube 2.2.3

**Compatible con versiones de Adobe Commerce:** Adobe Commerce (todos los métodos de implementación) 2.3.0-2.3.4-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Corrige el problema que se producía cuando después de importar un(a) `.csv` para actualizar las existencias del producto se eliminaban las filas de la tabla `cataloginventory_stock`.

<u>Pasos a seguir:</u>

1. En la base de datos ejecute el siguiente comando MySQL: `select count(*) from cataloginventory_stock_status;`
1. Tenga en cuenta el número de filas.
1. Establezca crontab de la siguiente manera: `* * * * * /usr/bin/php <path to installation>/bin/magento cron:run  | grep -v "Ran jobs by schedule" >> <path to installation>/var/log/cron.log 2>&1`
1. Vaya al panel Administración en **Sistema** > **Herramientas** > **Administración de índices**.
1. Establecer indizadores en *Actualizar según lo programado.*
1. Vaya a **Sistema** > *Transferencia de datos* > **Exportar**.
1. Establecer **Tipo de entidad** igual a *Productos* > **Continuar**.
1. Abra el archivo guardado de `.csv` > Quitar todas las columnas excepto SKU y CANT.
1. Actualice la cantidad de todos los productos a 150.
1. Guarde el archivo `.csv`.
1. Vaya a **Sistema** > *Transferencia de datos* > **Importar**.
1. Establezca los siguientes valores:
   1. Tipo de entidad: *Productos*
   1. Comportamiento de importación: *Agregar/Actualizar*
   1. Mantenga el resto de valores predeterminados.
   1. Seleccione Archivo para seleccionar la hoja de cálculo del producto del catálogo.
1. Haga clic en **Comprobar datos** > **Importar**. Se tardan entre 5 y 10 minutos en llegar.
1. En la base de datos ejecute el siguiente comando MySQL:
   `select count(*) from cataloginventory_stock_status;`

<u>Resultado real:</u>

El número de filas de `cataloginventory_stock` disminuye después de la importación del CSV para actualizar el inventario de existencias.

<u>Resultado esperado:</u>

El número de filas de `cataloginventory_stock` debe ser el mismo después de la importación de CSV para actualizar el inventario.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
