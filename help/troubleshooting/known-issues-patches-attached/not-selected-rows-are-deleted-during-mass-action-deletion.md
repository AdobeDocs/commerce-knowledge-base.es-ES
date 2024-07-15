---
title: Se eliminaron más productos de los que se iniciaron durante la eliminación masiva en Administración
description: Este artículo proporciona un parche para el problema conocido de Adobe СCommerce en la infraestructura en la nube 2.2.3 relacionado con no haber seleccionado registros que se eliminen cuando se realiza una eliminación masiva en una cuadrícula en el administrador de Commerce.
exl-id: 0bfdc84e-0292-4702-a20e-bdbe67c111a2
feature: Admin Workspace, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# Se eliminaron más productos de los que se iniciaron durante la eliminación masiva en Administración

Este artículo proporciona un parche para el problema conocido de Adobe СCommerce en la infraestructura en la nube 2.2.3 relacionado con no haber seleccionado registros que se eliminen cuando se realiza una eliminación masiva en una cuadrícula en el administrador de Commerce.

## Problema

En el Administrador, si selecciona los registros de cliente o cliente que desea eliminar, filtra la cuadrícula y, a continuación, selecciona la acción **Eliminar**, se eliminarán todos los registros.

<u>Pasos a seguir</u>:

1. Vaya a **Catálogo** > **Productos** en el Administrador.
1. Seleccione uno o varios productos.
1. Seleccione Eliminar en el menú desplegable Acciones.

<u>Resultados esperados</u>:

Solo se eliminan los productos seleccionados.

<u>Resultados reales</u>:

Algunos otros productos también se eliminan.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[Descargar MDVA-10600\_EE\_2.2.3\_v1.composer.patch](assets/MDVA-10600_EE_2.2.3_v1.composer.patch.zip)

### Versiones de Adobe Commerce compatibles:

El parche se ha creado para:

* Adobe Commerce en la infraestructura en la nube 2.2.3

El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce local 2.1.8-2.1.14, 2.2.0-2.2.2 y 2.2.4-2.2.5
* Adobe Commerce en infraestructura en la nube 2.2.4-2.2.5

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obtener instrucciones.
