---
title: Error tras iniciar sesión en el administrador de Commerce
description: Este artículo proporciona una solución para el problema en el que recibe un mensaje de error que indica que la dirección URL solicitada no se encontró en este servidor.
exl-id: f52b383b-87f2-4216-9bf4-e765db31ca6b
feature: Admin Workspace
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Error tras iniciar sesión en el administrador de Commerce

Este artículo proporciona una solución para el problema en el que recibe un mensaje de error que indica que la dirección URL solicitada no se encontró en este servidor.

## Detalles

La dirección URL solicitada /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ no se ha encontrado en este servidor.

Observe la falta de un carácter de barra diagonal entre `magento2` y `index.php` en la dirección URL.

## Solución

La URL de base no es correcta. La dirección URL base debe:

* Iniciar con `http://` o `https://`
* Finalizar con una barra diagonal ( `/` )
* Coincida con las mayúsculas y minúsculas del registro `web/unsecure/base_url` de la tabla de base de datos `core_config_data`

Vuelva a ejecutar la instalación con un valor válido.
