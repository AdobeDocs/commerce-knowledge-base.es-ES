---
title: Los usuarios no pueden añadir un producto al carro de compras si no se ha seleccionado nada en Permitir países
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.4.4 con PHP 8.1 en el que los usuarios no pueden añadir productos al carro de compras si la opción Permitir países no está seleccionada.
exl-id: d05d1956-de23-496c-9234-c461a3cfdf36
feature: Orders, Products, Shopping Cart
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# Los usuarios no pueden añadir un producto al carro de compras si no se ha seleccionado nada en Permitir países

Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.4.4 con PHP 8.1 en el que los usuarios no pueden añadir productos al carro de compras si la opción Permitir países no está seleccionada.

## Productos y versiones afectados

Adobe Commerce 2.4.4 con PHP 8.1

## Problema

Los usuarios no pueden añadir productos al carro de compras si la opción Permitir países no está seleccionada.

<u>Pasos a seguir</u>:

1. Inicie sesión en el administrador de Commerce.
1. Ir a **Tienda** > **Configuración** > **General** > **Opciones de país**
1. Anule la selección de todas las opciones del campo **Permitir países**.
1. Haga clic en **Guardar configuración** para guardar la configuración.
1. Vaya a la tienda e intente agregar un producto al carro de compras.

<u>Resultado esperado:</u>

Puede añadir un producto al carro de compras.

<u>Resultado real:</u>

No puede añadir un producto al carro de compras. Recibe el siguiente error de la consola:

```bash
Failed to load resource: the server responded with a status of 400 (Bad Request)
customer-data.js:87 Uncaught Error: [object Object]
    at Object.<anonymous> (customer-data.js:87:23)
    at fire (jquery.js:3500:50)
    at Object.fireWith [as rejectWith] (jquery.js:3630:29)
    at done (jquery.js:9798:30)
    at XMLHttpRequest.<anonymous> (jquery.js:10057:37)
```

## Causa

La configuración de Adobe Commerce recupera `null` en caso de que una configuración de selección múltiple no tenga elementos seleccionados. Esta configuración se procesaba correctamente en versiones de PHP anteriores a la 8.1. Sin embargo, en PHP 8.1 no funciona correctamente debido a los errores que causan &quot;[Deprecate pasa argumentos nulos a no admisibles de funciones internas en PHP 8.1](https://wiki.php.net/rfc/deprecate_null_to_scalar_internal_arg)&quot;.

## Soluciones

Para resolver el problema, aplique el siguiente parche:

[AC-2655_2.4.4.patch.zip](assets/AC-2655_2.4.4.patch.zip)

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de asistencia para obtener instrucciones.

## Vínculos útiles

[Aplique parches personalizados a Adobe Commerce en la infraestructura en la nube](https://devdocs.magento.com/guides/v2.3/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.
