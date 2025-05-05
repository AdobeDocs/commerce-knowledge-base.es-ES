---
title: 'Cambios incompatibles con versiones anteriores para [!DNL GraphQL] &grave;placeOrder&grave; [!DNL API] en Adobe Commerce 2.4.6-p8'
promoted: true
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce versión 2.4.6-p8 Cloud and On-premise en el que placeOrder [!DNL GraphQL API] no devuelve una respuesta de error esperada, como se vio en versiones de parches anteriores 2.4.6. Esto puede generar una experiencia de cierre de compra interrumpida para los comerciantes que usen una tienda de PWA o cualquier otra tienda basada en  [!DNL GraphQL API] para sus tiendas.
feature: Checkout, REST, GraphQL
role: Developer
source-git-commit: 01b79c75df34de20f1ff50ab40c0a8d608ffa779
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Cambios incompatibles con versiones anteriores para [!DNL GraphQL] `placeOrder` [!DNL API] en Adobe Commerce 2.4.6-p8

Este artículo proporciona un parche para el problema conocido de Adobe Commerce versión 2.4.6-p8 Cloud and On-premise en el que `placeOrder` [!DNL GraphQL API] no devuelve una respuesta de error esperada, como se vio en las versiones de parche anteriores de la versión 2.4.6. Esto puede generar una experiencia de cierre de compra interrumpida para los comerciantes que usen la tienda [!DNL PWA] o cualquier otra tienda basada en [!DNL GraphQL API] para sus tiendas.

>[!NOTE]
>
>Póngase en contacto con los servicios de soporte si tiene algún problema al aplicar el parche.

## Productos y versiones afectados

* Adobe Commerce en la nube 2.4.6-p8
* Adobe Commerce local 2.4.6-p8

## Problema

Después de la actualización en el parche de solo seguridad de Adobe Commerce 2.4.6-p8, [`placeOrder` [!DNL GraphQL API]](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/place-order/) no devuelve una respuesta de error esperada, como se ha visto en cualquier versión de parche anterior de la versión 2.4.6. Esto puede generar una experiencia de cierre de compra interrumpida para los comerciantes que usen la tienda [!DNL PWA] o cualquier otra tienda basada en [!DNL GraphQL API] para sus tiendas.

<u>Paso para reproducir</u>:

Ejecute la solicitud `placeOrder` [!DNL GraphQL] donde espera una respuesta de error.

<u>Resultado esperado</u>:

Recibirá una respuesta de error esperada.

<u>Resultado real</u>:

En lugar de una respuesta de error esperada, recibe una respuesta correcta, pero con una nueva clave `errors` con este aspecto:

```
{
    "data": {
        "placeOrder": {
            "order": null,
            "__typename": "PlaceOrderOutput"
        }
    }
}
```

## Solución para el software local de Adobe Commerce en la nube y Adobe Commerce

Para resolver el problema, aplique el parche.
Para descargarlo, haga clic en el siguiente vínculo:

[ac-13283-composer-patch.zip](assets/ac-13283-composer-patch.zip)

## Cómo aplicar el parche

Descomprima el archivo y vea [Cómo aplicar un parche del compositor proporcionado por el Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) en nuestra base de conocimiento de asistencia para obtener instrucciones.

## Solo para comerciantes de Adobe Commerce en la nube: cómo saber si se han aplicado los parches

Teniendo en cuenta que no es posible comprobar fácilmente si el problema se ha corregido, es posible que desee comprobar si el parche se ha aplicado correctamente.

<u>Para ello, siga los siguientes pasos y use el archivo de muestra `VULN-27015-2.4.7_COMPOSER.patch` **como ejemplo</u>**:

1. [Instalar [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Ejecute el comando:<br>
   ![ac-13283-tell-if-patch-applied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. Debería ver una salida similar a esta, donde VULN-27015 devuelve el estado *Aplicado*:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->

