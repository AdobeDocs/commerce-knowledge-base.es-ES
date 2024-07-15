---
title: '"Error 500" después de hacer doble clic en Eliminar vínculo en el carro de compras'
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce en la infraestructura en la nube 2.2.0 relacionado con los clientes que obtienen un error al intentar eliminar dos veces un elemento del carro de compras (haciendo doble clic en el vínculo *Eliminar* o haciendo clic en él en diferentes pestañas).
exl-id: 927cf681-febf-42cc-8db5-469bcf8f2012
feature: Orders, Shopping Cart
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# &quot;Error 500&quot; después de hacer doble clic en Eliminar vínculo en el carro de compras

Este artículo proporciona un parche para el problema conocido de Adobe Commerce en la infraestructura en la nube 2.2.0 relacionado con los clientes que reciben un error al intentar eliminar dos veces un elemento del carro de compras (haciendo doble clic en el vínculo *Quitar* o haciendo clic en él en diferentes pestañas).

## Problema

Cuando los clientes hacen doble clic en el vínculo *Quitar* del carro de compras, al intentar quitar un producto de este, obtienen una página en blanco con el siguiente mensaje de error: *&quot;Esta página no funciona. ERROR HTTP 500&quot;.* El mismo problema sucede si un cliente abre dos pestañas del explorador con la página del carro de compras y quita el producto primero en una pestaña y luego en la segunda.

<u>Pasos a seguir</u> :

1. Agregar un producto al carro de compras en la tienda.
1. Vaya a la página del carro de compras.
1. Haga doble clic en el vínculo Remove.

O

1. Agregar un producto al carro de compras en la tienda.
1. Vaya a la página del carro de compras.
1. Abra una nueva pestaña del explorador y vaya a la página del carro de compras (mismo producto).
1. Eliminar el producto del carro de compras.
1. Abra la segunda pestaña y vuelva a eliminar el producto.

<u>Resultado esperado</u> : El producto se ha eliminado del carro de compras sin errores.

<u>Resultado real</u> : El producto se eliminó con el error: *&quot;Esta página no funciona. Mensaje de error HTTP 500&quot;*.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[Descargar MDVA-8623\_EE\_2.2.0\_v1.composer.patch](assets/MDVA-8623_EE_2.2.0_v1.composer.patch.zip)

## Versiones de Adobe Commerce compatibles:

El parche se ha creado para:

* Adobe Commerce en la infraestructura en la nube 2.2.0

El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce en infraestructura en la nube 2.2.1 - 2.2.5
* Adobe Commerce local 2.2.0 - 2.2.5

## Cómo aplicar el parche

Para obtener instrucciones, consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de soporte.

## Archivos adjuntos
