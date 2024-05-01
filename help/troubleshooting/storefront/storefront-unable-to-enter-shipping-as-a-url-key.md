---
title: No se puede guardar "envío" como clave de URL
description: Este artículo proporciona una solución para el problema en el que no puede guardar el "envío" como clave de URL (por ejemplo, "/shipping") para productos o páginas de CMS. Cuando intente guardar la clave URL, recibirá un error que indica que se trata de una URL duplicada.
exl-id: df19b597-f615-4b19-82c1-59cc179fa720
feature: Marketing Tools, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# No se puede guardar &quot;envío&quot; como clave de URL

Este artículo proporciona una solución para el problema en el que no puede guardar el &quot;envío&quot; como clave de URL (por ejemplo, &quot;/shipping&quot;) para productos o páginas de CMS. Cuando intente guardar la clave URL, recibirá un error que indica que se trata de una URL duplicada.

## Productos y versiones afectados

Adobe Commerce (todos los métodos de implementación) 2.4.x

## Problema

No puede guardar una página de CMS con el término &quot;envío&quot; en la clave URL.

<u>Pasos a seguir</u>:

Cree una página de CMS con la clave de URL como &quot;envío&quot;.

<u>Resultado esperado</u>:

La página guarda los datos con &quot;envío&quot; en la clave URL.

<u>Resultado real</u>:

No puede guardar y aparece un error: *El valor especificado en el campo Clave de URL generaría una dirección URL que ya existe.*

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

No puedes usar el término &quot;envío&quot; en tu clave de URL; sin embargo, puedes usar el término &quot;envío&quot; combinado con otra letra o número (por ejemplo, &quot;envío1&quot; y &quot;envío2&quot;). Aunque el término no tiene que ser &quot;shipping&quot;+&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;> : el término puede ser cualquier cadena siempre que la longitud no supere los 255 caracteres.

Siga estos pasos:

1. Inicie sesión en el administrador de Commerce.
1. Ir a **Marketing** > SEO y búsqueda > **Reescrituras de URL**.
1. Clic **Añadir reescritura de URL**.
1. Seleccionar *Personalizado* en la lista desplegable Crear reescritura de URL.
   1. Escriba la ruta de solicitud &quot;envío&quot;. Nota: La ruta de solicitud es lo que introduce un usuario en el explorador y la ruta de destino es a dónde debe redirigirse.
   1. Escriba en la Ruta de destino la nueva clave de URL (por ejemplo, &quot;shipping1&quot;).
   1. Seleccionar **No** en la lista desplegable Redireccionamiento.

## Lectura relacionada

* [Reescrituras de URL](https://docs.magento.com/user-guide/marketing/url-rewrite.html) en nuestra guía del usuario.
* [Prácticas recomendadas de SEO](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) en nuestra guía del usuario.
