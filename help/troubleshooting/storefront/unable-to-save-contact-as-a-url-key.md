---
title: No se puede guardar *contacto* como clave de URL
description: Este artículo proporciona una solución al problema cuando no puede guardar *contacto* como clave URL (por ejemplo, "/contacto") para productos o páginas de CMS. Cuando intente guardar la clave URL, recibirá un error que indica que se trata de una URL duplicada.
exl-id: eb340813-aba5-43a4-af5d-8fb64c93e021
feature: CMS, Marketing Tools, Storefront
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# No se puede guardar *contact* como clave de URL

Este artículo proporciona una solución al problema cuando no puede guardar *contact* como una clave de URL (por ejemplo, &quot;/contact&quot;) para productos o páginas de CMS.

## Productos y versiones afectados

Adobe Commerce (todos los métodos de implementación) 2.4.x

## Problema

No puede guardar un producto o una página de CMS usando el término *contact* como clave de URL. Cuando intente guardar la clave URL, recibirá un error que indica que se trata de una URL duplicada.

<u>Pasos a seguir</u>:

Cree una página de CMS con *contact* como clave de URL.

<u>Resultado esperado</u>:

La página se guardó con *contact* como clave de URL.

<u>Resultado real</u>:

No puede guardar la página. Recibe el error: *El valor especificado en el campo Clave de dirección URL generaría una dirección URL que ya existe.*

## Causa

*Contacto* es una palabra reservada definida en `vendor/magento/module-contact/view/frontend/layout/contact_index_index.xml`.

```xml
<router id="standard">
      <route id="contact" frontName="contact">
          <module name="Magento_Contact" />
      </route>
  </router>
```

## Solución

No puedes usar el término *contacto* como clave de URL, pero puedes usar el término *contacto* combinado con otra letra o número (por ejemplo, *contacto1* y *contacto2*). Aunque el término no tiene que ser *contact+\&lt;otro número o letra\>*, podría ser cualquier cadena siempre que la longitud no supere los 255 caracteres.

Siga estos pasos:

1. Inicie sesión en Commerce Admin.
1. Vaya a **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. Haga clic en **[!UICONTROL Add URL Rewrite]**.
1. Seleccione *[!UICONTROL Custom]* en la lista desplegable [!UICONTROL Create URL Rewrite].
   1. En [!UICONTROL Request Path], escriba &quot;contacto&quot;. Tenga en cuenta que [!UICONTROL Request Path] es lo que un usuario introduce en el explorador y [!UICONTROL Target Path] es a donde debería redirigirse.
   1. En [!UICONTROL Target Path], escriba la nueva clave de dirección URL (por ejemplo, &quot;contact1&quot;).
   1. Seleccione *[!UICONTROL No]* en la lista desplegable [!UICONTROL Redirect].

## Lectura relacionada

* [Reescrituras de URL](https://docs.magento.com/user-guide/marketing/url-rewrite.html) en nuestra guía del usuario.
* [Prácticas recomendadas de SEO](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) en nuestra guía del usuario.
