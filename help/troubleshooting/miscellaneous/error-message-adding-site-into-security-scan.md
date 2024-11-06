---
title: Mensaje de error al añadir sitios al análisis de seguridad
description: Este artículo proporciona posibles soluciones para el problema cuando un usuario no puede agregar sitios al [Commerce Security Scan](https://account.magento.com/scanner/dashboard/).
exl-id: 8d000ca4-b977-432d-bb26-6ea320067a40
feature: Cache, Compliance, Console, Security
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '350'
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
   * 52 87 98 44
   * 34 196 167 176
   * 3.218.25.102

1. El código de confirmación distingue entre tiempo y minúsculas. Si han pasado más de 30 minutos desde que se hizo clic en el vínculo **Agregar sitio**, es probable que el código haya caducado.
1. No olvide limpiar la caché y asegurarse de que el código de validación aparece en el cuerpo de origen de la página principal. El código de confirmación debe insertarse según las especificaciones de marcado del HTML: el comentario del HTML se puede insertar en el cuerpo de la página (sugerimos colocarlo en la sección de pie de página); la etiqueta META debe estar solo en la sección del encabezado.
1. Antes de hacer clic en **Verificar código de confirmación**, abra la consola para desarrolladores del explorador, haga clic en la ficha **Red** y compruebe la respuesta en magento.com. Debe ser HTTP 200 (OK) y el cuerpo de la respuesta debe contener un objeto JSON.
1. Si el código de respuesta es HTTP 200 y el cuerpo de respuesta es un objeto JSON y el valor de la propiedad `verified` es `false`, significa que el código no se encuentra en la página. El valor de la propiedad `details` debe contener la explicación. Por ejemplo, si el almacén utiliza un certificado SSL autofirmado, probablemente se producirá un error de conexión.

Si sigue sin poder agregar sitios, complete los siguientes pasos:

1. Coloque otro comentario del HTML en la página:

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

* [Examen de seguridad](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan) en nuestra guía del usuario.
