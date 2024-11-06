---
title: Restablecer un tema a los valores predeterminados
description: Según los problemas que encuentre al personalizar las temáticas y desarrollar la tienda, es posible que no tenga acceso a través del administrador de Commerce. Puede borrar y restablecer la temática predeterminada sin acceder al administrador. Después de borrar la temática, se aplicará la predeterminada de Luma.
exl-id: 86304dd5-f448-4dcc-ad07-04ecc6c85b6d
feature: Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Restablecer un tema a los valores predeterminados

Según los problemas que encuentre al personalizar las temáticas y desarrollar la tienda, es posible que no tenga acceso a través del administrador de Commerce. Puede borrar y restablecer la temática predeterminada sin acceder al administrador. Después de borrar la temática, se aplicará la predeterminada de Luma.

Mientras desarrolla Adobe Commerce (todas las implementaciones) y componentes de Magento Open Source (módulos, temáticas y paquetes de idiomas), su entorno, que cambia rápidamente, requiere que borre periódicamente ciertos directorios y cachés. De lo contrario, el código se ejecuta con excepciones y no funcionará correctamente. Para obtener más información, consulte [Borrar directorios durante el desarrollo](https://developer.adobe.com/commerce/php/development/components/clear-directories/) en nuestra documentación para desarrolladores.

## Entorno y tecnologías

* Adobe Commerce local
* Adobe Commerce en la infraestructura en la nube
* Magento Open Source

## Requisitos previos

* Herramientas de base de datos

## Pasos

Si necesita restablecer la temática de la tienda, pero no puede acceder al panel de administración, puede hacerlo en la base de datos haciendo lo siguiente:

1. Use una herramienta de base de datos como [phpMyAdmin](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) o acceda a la base de datos manualmente desde la línea de comandos para ejecutar la siguiente consulta SQL: `UPDATE core_config_data SET value=NULL WHERE path='design/theme/theme_id'`
1. Borre los siguientes directorios:
   * `pub/static/frontend`
   * `var/view_preprocessing`
   * `var/cache`
   * `var/page_cache`

De este modo, no habrá ningún tema definido en el nivel de vista de tienda y, cuando vuelva a cargar las páginas principales de la tienda, se aplicará el tema predeterminado de Luma.

## Información adicional

* [Borrar directorios durante el desarrollo](https://developer.adobe.com/commerce/php/development/components/clear-directories/) en nuestra documentación para desarrolladores
