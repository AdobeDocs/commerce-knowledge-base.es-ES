---
title: Error de versión de PHP o error 404 al acceder a Adobe Commerce en el explorador
description: Este artículo proporciona soluciones para los problemas en los que no puede acceder a su instancia de Adobe Commerce en un navegador web y obtener error 404 o error de "versión de PHP no compatible".
exl-id: 6cfdeaae-5e52-411c-9006-5af8a467873a
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Error de versión de PHP o error 404 al acceder a Adobe Commerce en el explorador

Este artículo proporciona soluciones para los problemas en los que no puede acceder a su instancia de Adobe Commerce en un navegador web y obtener error 404 o error de &quot;versión de PHP no compatible&quot;.

## Productos y versiones afectados:

* Adobe Commerce 2.3.x

## Problema: versión de PHP no compatible

El siguiente mensaje se muestra cuando intenta acceder a la tienda de Adobe Commerce o al administrador de Commerce:

`Magento supports PHP 7.1.3 or later. Please read Magento System Requirements.`

### Solución

Pruebe lo siguiente:

* Actualice PHP a la versión 7.3. Para obtener más información, consulte [Requisitos de pila de tecnología Adobe Commerce 2.3](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements) en nuestra documentación para desarrolladores.
* Reinicie Apache, ya que es posible que no utilice la misma versión de PHP que en el sistema de archivos. Para reiniciar Apache, utilice los siguientes comandos:
   * Ubuntu: `service apache2 restart`
   * CentOS: `service httpd restart`

## Problema: error 404

Se muestra un error 404 (no encontrado) al intentar acceder a la tienda de Adobe Commerce o al administrador de Commerce.

### Solución

Pruebe lo siguiente:

* Asegúrese de que las [reescrituras del servidor Apache](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/web-server/apache) estén habilitadas. Si las reescrituras del servidor Apache están configuradas incorrectamente, los archivos estáticos no se proporcionan desde la ubicación correcta.
* Es posible que haya un problema con la dirección URL base que introdujo durante la instalación. La dirección URL base se especifica como el valor de `--base-url=` al instalar Adobe Commerce desde la línea de comandos o como el valor del campo **Su dirección de almacén** en la página Configuración web del instalador web. La dirección URL base *debe* comenzar con el esquema (como `http://` ) y finalizar con una barra diagonal (/). Vuelva a ejecutar el instalador con un valor válido e intente acceder a Adobe Commerce más tarde.
