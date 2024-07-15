---
title: Solucionar problemas de la página Crear pedido en modo restringido [!UICONTROL CSP]
description: Este artículo explica los errores que se producen al crear un pedido en el lado del administrador cuando el modo restringido CSP está habilitado y proporciona soluciones para corregirlos.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: c1a0886a-df1f-418a-9e4d-562b28a0d8b3
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# Solucionar problemas de la página Crear pedido en modo restringido [!UICONTROL CSP]

Este artículo proporciona explicaciones y correcciones para los problemas de Adobe Commerce 2.4.7 mientras se crea un pedido en el lado del administrador con **[!UICONTROL CSP restricted mode]** está *Habilitado*, con el &quot;*Se rechazó ejecutar script en línea porque infringe la siguiente directiva de directiva de seguridad de contenido: &quot;script-src ...*&quot; mensaje de error en el registro de la consola del explorador.

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube, Adobe Commerce local y Magento Open Source:

* 2.4.7
* 2.4.6-pX
* 2,4,5-pX
* 2.4.4-pX

## Problema - La página del administrador **crear pedido** está dañada o no se puede cargar

La página de administración **create order** está dañada o no se puede cargar, con el script en línea &quot;*No se pudo ejecutar porque infringe la siguiente directiva de directiva de seguridad de contenido: &quot;script-src ...*&quot; mensaje de error en el registro de la consola del explorador.

<u>Pasos a seguir</u>:

1. Ir a **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Cree un nuevo pedido.

<u>Resultados esperados</u>:

La página Administrador **crear pedido** se carga completamente normalmente.

<u>Resultados reales</u>:

La página Administrador **crear pedido** está en blanco o faltan componentes. El siguiente error [!DNL JS] se muestra en el registro de la consola del explorador: &quot;*Se rechazó ejecutar script en línea porque infringe la siguiente directiva de directiva de seguridad de contenido: &quot;script-src ...*&quot;

### Causa

En la versión 2.4.7 y posteriores de Adobe Commerce y Magento Open Source, **[!UICONTROL CSP]** está configurado en `restrict-mode`, de forma predeterminada, para las páginas de pago en las áreas de tienda y administración, y en el modo `report-only` para todas las demás páginas.
El encabezado **[!UICONTROL CSP]** correspondiente no contiene la palabra clave `unsafe-inline` dentro de la directiva `script-src` para páginas de pago. Además, solo se permiten [!DNL whitelisted] scripts en línea.

### Solución

Los usuarios pueden ver errores en el explorador debido a que se han bloqueado ciertos scripts debido a [!UICONTROL CSP]:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u>Para solucionar este problema, debe</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) los scripts bloqueados mediante la clase `SecureHtmlRenderer`.
1. Utilice la clase `CSPNonceProvider` para permitir la ejecución de scripts.
Adobe Commerce y Magento Open Source 2.4.7 y versiones posteriores incluyen un proveedor **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] para facilitar la generación de cadenas [!DNL nonce] únicas para cada solicitud. Estas cadenas de [!DNL nonce] se adjuntan al encabezado [!UICONTROL CSP].

   Utilice la función `generateNonce` en `Magento\Csp\Helper\CspNonceProvider` para obtener una cadena [!DNL nonce].

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [Agregue [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) al archivo `csp_whitelist.xml` de su módulo.

## Problema: falta el método de pago o no funciona

Falta el método de pago o no funciona en la página de creación de pedidos **del administrador**, con el script en línea &quot;*Rechazado porque infringe la siguiente directiva de directiva de seguridad de contenido: &quot;script-src ...*&quot; mensaje de error en el registro de la consola del explorador.

<u>Pasos a seguir</u>:

1. Ir a **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Cree un nuevo pedido.
1. Crear un cliente nuevo.
1. Introduzca los detalles del cliente.
1. Introduzca los detalles del pedido (productos, método de envío).
1. Seleccione una forma de pago.

<u>Resultados esperados</u>:

Puede seleccionar una forma de pago y proceder a realizar un pedido correctamente.

<u>Resultados reales</u>:

El método de pago falta o no funciona. El siguiente error [!DNL JS] se muestra en el registro de la consola del explorador: &quot;*Se rechazó ejecutar script en línea porque infringe la siguiente directiva de directiva de seguridad de contenido: &quot;script-src ...*&quot;.

### Causa

En la versión 2.4.7 y posteriores de Adobe Commerce y Magento Open Source, **[!UICONTROL CSP]** está configurado en `restrict-mode`, de forma predeterminada, para las páginas de pago en las áreas de tienda y administración, y en el modo `report-only` para todas las demás páginas.
El encabezado **[!UICONTROL CSP]** correspondiente no contiene la palabra clave `unsafe-inline` dentro de la directiva `script-src` para páginas de pago. Además, solo se permiten [!DNL whitelisted] scripts en línea.

### Solución

Los usuarios pueden ver errores en el explorador debido a que se han bloqueado ciertos scripts debido a **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u>Para solucionar este problema, debe</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) los scripts bloqueados mediante la clase `SecureHtmlRenderer`.
1. Utilice la clase `CSPNonceProvider` para permitir la ejecución de scripts.
Adobe Commerce y Magento Open Source 2.4.7 y versiones posteriores incluyen un proveedor **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] para facilitar la generación de cadenas [!DNL nonce] únicas para cada solicitud. Estas cadenas de [!DNL nonce] se adjuntan al encabezado [!UICONTROL CSP].

   Utilice la función `generateNonce` en `Magento\Csp\Helper\CspNonceProvider` para obtener una cadena [!DNL nonce].

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [agrega [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) al archivo `csp_whitelist.xml` de tu módulo.

## Problema: el administrador no puede realizar un pedido

Un administrador no puede enviar una solicitud en la página de administración **crear pedido**, con el script en línea &quot;*Se rechazó ejecutar porque infringe la siguiente directiva de directiva de seguridad de contenido: &quot;script-src ...*&quot; mensaje de error en el registro de la consola del explorador.

<u>Pasos a seguir</u>:

1. Ir a **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Cree un nuevo pedido.
1. Crear un cliente nuevo.
1. Introduzca los detalles del cliente.
1. Introduzca los detalles del pedido (productos, método de envío).
1. Seleccione una forma de pago.
1. Envíe el pedido.

<u>Resultados esperados</u>:

Puede enviar una solicitud correctamente.

<u>Resultados reales</u>:

No es posible enviar una solicitud. El siguiente error [!DNL JS] se muestra en el registro de la consola del explorador: &quot;*Se rechazó ejecutar script en línea porque infringe la siguiente directiva de directiva de seguridad de contenido: &quot;script-src ...*&quot;

### Causa

En la versión 2.4.7 y posteriores de Adobe Commerce y Magento Open Source, **[!UICONTROL CSP]** está configurado en `restrict-mode`, de forma predeterminada, para las páginas de pago en las áreas de tienda y administración, y en el modo `report-only` para todas las demás páginas.
El encabezado **[!UICONTROL CSP]** correspondiente no contiene la palabra clave `unsafe-inline` dentro de la directiva `script-src` para páginas de pago. Además, solo se permiten [!DNL whitelisted] scripts en línea.

### Solución

Los usuarios pueden ver errores en el explorador debido a que se han bloqueado ciertos scripts debido a **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u>Para solucionar este problema, debe</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) los scripts bloqueados mediante la clase `SecureHtmlRenderer`.
1. Utilice la clase `CSPNonceProvider` para permitir la ejecución de scripts.
Adobe Commerce y Magento Open Source 2.4.7 y versiones posteriores incluyen un proveedor **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] para facilitar la generación de cadenas [!DNL nonce] únicas para cada solicitud. Estas cadenas de [!DNL nonce] se adjuntan al encabezado [!UICONTROL CSP].

   Utilice la función `generateNonce` en `Magento\Csp\Helper\CspNonceProvider` para obtener una cadena [!DNL nonce].

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [Agregue [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) al archivo `csp_whitelist.xml` de su módulo.
