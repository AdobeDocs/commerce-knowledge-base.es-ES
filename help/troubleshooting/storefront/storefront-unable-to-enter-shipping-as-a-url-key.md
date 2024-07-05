---
title: No se puede guardar el envío como clave de URL
description: Este artículo proporciona una solución para el problema cuando no puede guardar el envío como una clave URL (_p. ej., /shipping_) para productos o páginas de CMS. Cuando intente guardar la clave URL, recibirá un error que indica que se trata de un duplicado de una dirección URL.
exl-id: df19b597-f615-4b19-82c1-59cc179fa720
feature: Marketing Tools, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 1ce963142a261a17e2b42f79dd567c8484ec5b3e
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# No se puede guardar _envío_ como clave URL

Este artículo proporciona una solución al problema cuando no puede guardar el envío como clave de URL (_por ejemplo, /shipping_) para productos o páginas de CMS. Cuando intente guardar la clave URL, recibirá un error que indica que se trata de una URL duplicada.

## Productos y versiones afectados

Adobe Commerce (todos los métodos de implementación) 2.4.x

## Problema

No puede guardar una página de CMS con el término _envío_ en la clave URL.

<u>Pasos a seguir</u>:

Crear un **[!UICONTROL CMS page]** con la clave URL como _envío_.

<u>Resultado esperado</u>:

La página guarda con _envío_ como clave de URL.

<u>Resultado real</u>:

No puede guardar debido a que se produce este error:
*El valor especificado en el campo Clave de URL generaría una dirección URL que ya existe.*

## Causa

Envío es una palabra reservada definida en `vendor/magento/module-shipping/etc/frontend/routes.xml`.

```xml
<router id="standard">
      <route id="shipping" frontName="shipping">
          <module name="Magento_Shipping" />
      </route>
  </router>
```

## Solución

No puede usar el término _envío_ en la clave URL, aunque puede usar el término _envío_ combinado con otra letra o número (_Por ejemplo, shipping1 y shipping2_).

Aunque el término no tiene que ser _envío_+&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;> : el término puede ser cualquier cadena siempre que la longitud no supere *255* caracteres.

## Siga estos pasos:

1. Inicie sesión en el administrador de Adobe Commerce.
1. Ir a **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. Clic **[!UICONTROL Add URL Rewrite]**.
1. Seleccionar **[!UICONTROL Custom]** en el **[!UICONTROL Create URL Rewrite]** menú desplegable.
   1. Escriba el [!UICONTROL Request Path] as **_envío_**.
   1. En el **[!UICONTROL Target Path]**, escriba la nueva clave de URL (_Por ejemplo, &quot;shipping1&quot;_).
   1. Seleccionar **[!UICONTROL No]** en el **[!UICONTROL Redirect]** menú desplegable.


      (**Nota**: la ruta de solicitud es lo que introduce un usuario en el explorador y la ruta de destino es a donde debe redirigirse.)

Además, evite utilizar estas palabras clave con la etiqueta *reservado* palabras clave que hacen que aparezca la misma excepción. El uso de cualquiera de estas palabras clave enumeradas a continuación como valor de clave URL provocará que aparezca el mismo error.


```
"admin"
"adminAnalytics"
"analytics"
"api"
"backup"
"bulk"
"captcha"
"catalog"
"catalogsearch"
"checkout"
"cms"
"contact"
"cookie"
"customer"
"directory"
"downloadable"
"giftmessage"
"groupedProduct"
"indexer"
"instantpurchase"
"loginascustomer"
"marketplace"
"mui"
"multishipping"
"newsletter"
"oauth"
"paypal"
"persistent"
"productalert"
"releaseNotification"
"reports"
"review"
"robots"
"rss"
"sales"
"search"
"security"
"sendfriend"
"shipping"
"stores"
"swagger"
"swatches"
"tax"
"theme"
"translation"
"vault"
"wishlist"
```

## Lectura relacionada

* [Reescrituras de URL](https://docs.magento.com/user-guide/marketing/url-rewrite.html) en nuestra Guía del usuario de promociones y comercialización.
* [Prácticas recomendadas de SEO](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) en nuestra Guía del usuario de promociones y comercialización.
