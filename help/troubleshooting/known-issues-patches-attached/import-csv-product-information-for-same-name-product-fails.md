---
title: Error al importar información de producto CSV para el mismo producto con nombre
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.2.3 relacionado con la obtención de errores al intentar importar un archivo ".csv" con información de productos si hay productos con el mismo nombre.
exl-id: 420b0283-455a-4bd5-ba51-18f341ddacd5
feature: Data Import/Export, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Error al importar información de producto CSV para el mismo producto con nombre

Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.2.3 relacionado con la obtención de errores al intentar importar una `.csv` archivo con información de productos si hay productos con el mismo nombre.

## Problema

Cuando un `.csv` Cuando se importa un archivo con información de productos y hay productos con el mismo nombre, aparece el siguiente error en el paso Comprobar datos: *&quot;`URL Key XYZ was already generated for an item with the SKU %sku%"`*. El problema se debe a que se vuelven a escribir las direcciones URL de los productos durante la importación, incluso cuando no hay ninguna columna para las direcciones URL de los productos en la importación `.csv` archivo.

<u>Pasos a seguir</u>:

1. Cree dos productos configurables con el mismo nombre en el Administrador de Commerce.
1. Crear un `.csv` para importar los datos de esos productos, que tiene, por ejemplo, estas columnas: `sku` | `product_type` | `name` | `product_websites` | `store_view_code`
1. Ir a **Sistema** > **Transferencia de datos** > **Importar** y seleccione la `.csv` archivo.
1. Clic **Comprobar datos**.

<u>Resultado esperado</u>:

No se han encontrado problemas; puede importar el `.csv` archivo correctamente.

<u>Resultado real</u>:

Se muestra el siguiente mensaje de error: *&quot;La clave URL XYZ ya se generó para un artículo con el SKU %sku%&quot;* No obstante, no es posible importar el archivo.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[Descargar MDVA-12899\_EE\_2.2.3\_COMPOSER\_v2.patch](assets/MDVA-12899_EE_2.2.3_COMPOSER_v2.patch.zip)

### Versiones de Adobe Commerce compatibles:

El parche se ha creado para:

* Adobe Commerce local 2.2.3

El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes ediciones y versiones de Adobe Commerce:

* Adobe Commerce en la infraestructura en la nube de 2.2.0 a 2.2.7 y 2.3.0
* Adobe Commerce local de 2.2.0 a 2.2.2, de 2.2.4 a 2.2.7 y 2.3.0

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de asistencia para obtener instrucciones.

## Vínculos útiles

[Aplicar parches personalizados a Adobe Commerce en la infraestructura en la nube](https://devdocs.magento.com/guides/v2.3/cloud/project/project-patch.html)

## Archivos adjuntos
