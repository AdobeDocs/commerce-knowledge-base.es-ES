---
title: Después de la instalación, las imágenes y las hojas de estilo no se cargan; solo se muestra texto, sin gráficos
description: En este artículo se describen los posibles motivos y soluciones del problema por el que las hojas de estilo y las imágenes no se cargan después de instalar Adobe Commerce.
exl-id: f33cee89-b416-4d63-8cc5-9cc57618ce92
feature: Install, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# Después de la instalación, las imágenes y las hojas de estilo no se cargan; solo se muestra texto, sin gráficos

En este artículo se describen los posibles motivos y soluciones del problema por el que las hojas de estilo y las imágenes no se cargan después de instalar Adobe Commerce.

## Productos y versiones afectados

* Adobe Commerce 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Problema

<u>Pasos a seguir</u>

1. Instale Adobe Commerce.
1. Vaya a la tienda o al administrador.

<u>Resultado esperado</u>

Si se aplican estilos, ningún elemento de la interfaz de usuario tiene el aspecto de estilos que faltan.

<u>Resultado real</u>

Los estilos no se aplican correctamente, faltan gráficos.

## Causa

La ruta a las imágenes y hojas de estilo no es correcta, ya sea debido a una URL base incorrecta o porque las reescrituras del servidor (CentOS, Ubuntu) no están configuradas correctamente.

Para confirmar que este es el caso, utilice un inspector del explorador web para comprobar las rutas a los recursos estáticos y comprobar que dichos recursos se encuentran en el sistema de archivos de Adobe Commerce o de Magento Open Source.

Los recursos estáticos se encuentran en `<magento_root>/pub/static/` , en los directorios `frontend` y `adminhtml`.

## Solución

Las siguientes son posibles soluciones según el software que utilice y la causa del problema:

* Si está usando el servidor web Apache, verifique la configuración de [reescribe el servidor](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/apache.html#apache-help-rewrite) y la URL base del servidor Adobe Commerce/Magento Open Source e inténtelo de nuevo. Si configuró la directiva Apache `AllowOverride` incorrectamente, los archivos estáticos no se proporcionan desde la ubicación correcta.
* Si está usando el servidor web nginx, asegúrese de [configurar un archivo host virtual](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/nginx.html#configure-nginx-ubuntu). El archivo host virtual nginx debe cumplir los siguientes criterios:
   * La directiva `include` debe apuntar al archivo de configuración nginx de ejemplo en el directorio de instalación de Adobe Commerce/Magento Open Source. Por ejemplo:    `include /var/www/html/magento2/nginx.conf.sample;`
   * La directiva `server_name` debe coincidir con la dirección URL base especificada al instalar Adobe Commerce/Magento Open Source. Por ejemplo: `server_name 192.186.33.10;`
* Si la aplicación se encuentra en [modo de producción](https://devdocs.magento.com/guides/v2.3/config-guide/bootstrap/magento-modes.html#production-mode), intente implementar archivos de vista estática mediante el comando `magento setup:static-content:deploy`. Para obtener más información sobre la implementación de archivos estáticos, consulte [Implementar archivos de vista estática](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-maint.html) en nuestra documentación para desarrolladores.
