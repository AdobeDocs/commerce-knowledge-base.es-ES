---
title: Error de página en blanco o bucle de redirección al acceder a la tienda o al administrador de Commerce
description: Este artículo proporciona una solución al problema cuando accede a la tienda o el back-end de Adobe Commerce y obtiene una página en blanco o un bucle de redirección.
exl-id: 65869de2-1939-481b-844b-69122345b407
feature: Admin Workspace, Cache, Storefront
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# Error de página en blanco o bucle de redirección al acceder a la tienda o al administrador de Commerce

Este artículo proporciona una solución al problema cuando accede a la tienda o el back-end de Adobe Commerce y obtiene una página en blanco o un bucle de redirección.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, todas las versiones
* Adobe Commerce local, todas las versiones
* Magento Open Source, todas las versiones

## Problema

<u>Pasos a seguir</u>

Abra una tienda o una página de administración.

<u>Resultado esperado</u>

Se abre la página.

<u>Resultado real</u>

La página está en blanco o muestra el mensaje de error *&quot;Esta página web tiene un bucle de redirección&quot;*.

## Causa

Una de las razones más probables del problema es que Adobe Commerce está configurado para redirigir desde una URL no segura a una URL segura, pero se proporciona una URL no segura como valor de la configuración de una URL segura.

Para solucionar el problema, debe corregir el valor del vínculo seguro.

## Solución

Para asegurarse de que esta sea la causa del problema, siga los siguientes pasos:

1. Compruebe el valor de `web/secure/enable_upgrade_insecure` , `web/secure/use_in_adminhtml` (si tiene el problema de redirección de bucle/blanco en Administración) o `web/secure/use_in_frontend` (si tiene el problema de redirección de bucle/blanco en la tienda) en la tabla de base de datos `'core_config_data'`.
   * Si `web/secure/enable_upgrade_insecure` se establece en &quot;1&quot;, entonces Adobe Commerce se configura para agregar el encabezado de respuesta `Content-Security-Policy: upgrade-insecure-requests`, dando instrucciones a los exploradores para que usen HTTPS y redireccionando todas las consultas que llegan a través de HTTP
a HTTPS, tanto para administración como para tienda.
   * Si `web/secure/use_in_adminhtml` se establece en &quot;1&quot;, Adobe Commerce devuelve redirecciones HTTPS para todas las solicitudes HTTP de las páginas de administración.
   * Si `web/secure/use_in_frontend` se establece en &quot;1&quot;, Adobe Commerce devuelve redirecciones HTTPS para todas las solicitudes HTTP de las páginas principales de la tienda.
1. Compruebe los valores `web/secure/base_url` y `web/unsecure/base_url` en la tabla `'core_config_data'`. Si ambos comienzan con    `http`, entonces debe corregir el valor &quot;secure&quot;.

Solucionando el problema:

1. Establecer el valor que comienza por `https` para `web/secure/base_url.`
1. Para que se apliquen los cambios, limpie la caché de configuración ejecutando el siguiente comando:

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```
