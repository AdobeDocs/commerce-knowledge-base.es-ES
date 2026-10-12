---
title: Mensaje de error al añadir sitios al análisis de seguridad
description: Este artículo proporciona posibles soluciones para el problema cuando un usuario no puede agregar sitios al [Commerce Security Scan](https://account.magento.com/scanner/dashboard/).
exl-id: 8d000ca4-b977-432d-bb26-6ea320067a40
feature: Cache, Compliance, Console, Security
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%
---
# Mensaje de error al añadir sitios al análisis de seguridad

Este artículo proporciona posibles soluciones para el problema cuando un usuario no puede agregar sitios al [análisis de seguridad de Commerce](https://account.magento.com/scanner/dashboard/).

## Productos y versiones afectados

* Adobe Commerce (todos los métodos y versiones de implementación)
* Magento Open Source

## Problema

El usuario no puede agregar sitios al [Examen de seguridad de Commerce](https://account.magento.com/scanner/dashboard/). El siguiente mensaje de error aparece al intentar agregar un sitio: *No se puede enviar el sitio para su análisis.*

## Solución

1. Asegúrese de que las siguientes direcciones IP no estén bloqueadas en los puertos 80 y 443:
   * 52.87.98.44
   * 34.196.167.176
   * 3.218.25.102

1. El código de confirmación distingue entre tiempo y minúsculas. Si han pasado más de 30 minutos desde que se hizo clic en el vínculo **Agregar sitio**, es probable que el código haya caducado.
1. No olvide limpiar la caché y asegurarse de que el código de validación aparece en el cuerpo de origen de la página principal. El código de confirmación debe insertarse según las especificaciones de marcado de HTML: El comentario de HTML se puede insertar en el cuerpo de la página (sugerimos colocarlo en la sección de pie de página); la etiqueta de META debe estar solo en la sección del encabezado.
1. Antes de hacer clic en **Verificar código de confirmación**, abra la consola para desarrolladores del explorador, haga clic en la ficha **Red** y compruebe la respuesta en magento.com. Debe ser HTTP 200 (OK) y el cuerpo de la respuesta debe contener un objeto JSON.
1. Si el código de respuesta es HTTP 200 y el cuerpo de respuesta es un objeto JSON y el valor de la propiedad `verified` es `false`, significa que el código no se encuentra en la página. El valor de la propiedad `details` debe contener la explicación. Por ejemplo, si el almacén utiliza un certificado SSL autofirmado, probablemente se producirá un error de conexión.

Si sigue sin poder agregar sitios, complete los siguientes pasos:

1. Coloque otro comentario de HTML en la página:

   ```HTML
   <!-- MAGEID:Your magento.com ID, EMAIL:your email address -->
   ```

1. Envíe un ticket de asistencia y proporcione la siguiente información:
   * URL de tienda Adobe Commerce
   * MAGEID + correo electrónico de cuenta Magento.com
   * Nombre + Apellidos
   * Nombre de empresa
   * Lista de correo electrónico de notificaciones separadas por comas

## Lectura relacionada

* [Examen de seguridad](https://experienceleague.adobe.com/es/docs/commerce-admin/systems/security/security-scan) en nuestra guía del usuario.
