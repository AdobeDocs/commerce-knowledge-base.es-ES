---
title: laminas/laminas-escaper 2.7.1 causa error en las páginas de front-end y administración de Adobe Commerce
description: Este artículo proporciona una solución al problema en el que el lanzamiento de laminas/laminas-escaper:2.7.1 rompe la funcionalidad de Adobe Commerce en la administración de productos, categorías y páginas de productos. Este problema se solucionará en Adobe Commerce 2.4.3.
exl-id: 89de6827-7b90-4f08-92fb-56ed31ae2672
feature: Admin Workspace, Categories
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# laminas/laminas-escaper 2.7.1 causa error en las páginas de front-end y administración de Adobe Commerce


## Productos y versiones afectados

* Adobe Commerce en nuestra arquitectura de nube 2.3.5+
* Adobe Commerce 2.3.5+

## Problema

Después de la actualización a laminas/laminas-escaper:2.7.1 se muestra un mensaje de error en la página.

<u>Pasos a seguir</u>:

Actualice laminas/laminas-escaper a 2.7.1.

<u>Resultado esperado</u>:

No hay error.

<u>Resultado real</u>:

Tras la actualización a laminas/laminas-escaper:2.7.1 aparece un mensaje de error en la página de edición del producto (o gestión del producto): *TypeError: rawurlencode() espera que el parámetro 1 sea una cadena, int indicado en /var/www/magento/vendor/laminas/laminas-escaper/src/Escaper.php:246*
Este error se produce en las páginas de front-end y administración, lo que provoca que el contenido de la página se distorsione.

## Causa

laminas/laminas-escaper 2.7.1 comenzó a utilizar una validación de tipo estricta para la clase Escaper.

## Solución

Ejecutar `composer require laminas/laminas-escaper:2.7.0` en el directorio raíz de cada proyecto.

## Lectura relacionada

Documentación de laminas: [escapador de láminas](https://docs.laminas.dev/laminas-escaper/)
