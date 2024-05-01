---
title: Solución de problemas al crear página de pedido en [!UICONTROL CSP] modo restringido
description: Este artículo explica los errores que se producen al crear un pedido en el lado del administrador cuando el modo restringido CSP está habilitado y proporciona soluciones para corregirlos.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: c1a0886a-df1f-418a-9e4d-562b28a0d8b3
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# Solución de problemas al crear página de pedido en [!UICONTROL CSP] modo restringido

Este artículo proporciona explicaciones y correcciones para los problemas de Adobe Commerce 2.4.7 al crear un pedido del lado del administrador con **[!UICONTROL CSP restricted mode]** es *Habilitado*, con el signo &quot;*Se ha rechazado ejecutar un script en línea porque infringe la siguiente directiva de directiva de política de seguridad de contenido: &quot;script-src ...* Mensaje de error &quot; en el registro de la consola del explorador.

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube, Adobe Commerce local y Magento Open Source:

* 2.4.7
* 2.4.6-pX
* 2,4,5-pX
* 2.4.4-pX

## Problema - Administrador **crear pedido** La página está rota o no se puede cargar

El administrador **crear pedido** La página está rota o no se puede cargar, con el signo &quot;*Se ha rechazado ejecutar un script en línea porque infringe la siguiente directiva de directiva de política de seguridad de contenido: &quot;script-src ...* Mensaje de error &quot; en el registro de la consola del explorador.

<u>Pasos a seguir</u>:

1. Ir a **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Cree un nuevo pedido.

<u>Resultados esperados</u>:

El administrador **crear pedido** La página se carga completamente normalmente.

<u>Resultados reales</u>:

El administrador **crear pedido** La página está en blanco o faltan componentes. Lo siguiente [!DNL JS] El error se muestra en el registro de la consola del explorador: &quot;*Se ha rechazado ejecutar un script en línea porque infringe la siguiente directiva de directiva de política de seguridad de contenido: &quot;script-src ...*&quot;

### Causa

En Adobe Commerce y Magento Open Source versión 2.4.7 y posteriores, **[!UICONTROL CSP]** está configurado en `restrict-mode`, de forma predeterminada, para las páginas de pago de las áreas de tienda y administración, y en `report-only` para todas las demás páginas.
El correspondiente **[!UICONTROL CSP]** el encabezado no contiene `unsafe-inline` palabra clave dentro de `script-src` directiva para páginas de pago. Además, solo [!DNL whitelisted] se permiten scripts en línea.

### Solución

Los usuarios pueden ver errores del explorador debido a que algunas secuencias de comandos se han bloqueado debido a [!UICONTROL CSP]:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u>Para solucionar este problema, debe hacer lo siguiente</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) los scripts bloqueados que utilizan `SecureHtmlRenderer` clase.
1. Utilice el `CSPNonceProvider` para permitir la ejecución de scripts.
Adobe Commerce y Magento Open Source 2.4.7 y posteriores incluyen una **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] proveedor para facilitar la generación de [!DNL nonce] cadenas para cada solicitud. Estos [!DNL nonce] a continuación, las cadenas se adjuntan al [!UICONTROL CSP] encabezado.

   Utilice el `generateNonce` función en `Magento\Csp\Helper\CspNonceProvider` para obtener una [!DNL nonce] cadena.

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

1. [Añadir un [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) al de su módulo `csp_whitelist.xml` archivo.

## Problema: falta el método de pago o no funciona

Falta la forma de pago o no funciona en el administrador **página de creación de pedidos**, con el signo &quot;*Se ha rechazado ejecutar un script en línea porque infringe la siguiente directiva de directiva de política de seguridad de contenido: &quot;script-src ...* Mensaje de error &quot; en el registro de la consola del explorador.

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

El método de pago falta o no funciona. Lo siguiente [!DNL JS] El error se muestra en el registro de la consola del explorador: &quot;*Se ha rechazado ejecutar un script en línea porque infringe la siguiente directiva de directiva de política de seguridad de contenido: &quot;script-src ...*&quot;.

### Causa

En Adobe Commerce y Magento Open Source versión 2.4.7 y posteriores, **[!UICONTROL CSP]** está configurado en `restrict-mode`, de forma predeterminada, para las páginas de pago de las áreas de tienda y administración, y en `report-only` para todas las demás páginas.
El correspondiente **[!UICONTROL CSP]** el encabezado no contiene `unsafe-inline` palabra clave dentro de `script-src` directiva para páginas de pago. Además, solo [!DNL whitelisted] se permiten scripts en línea.

### Solución

Los usuarios pueden ver errores del explorador debido a que algunas secuencias de comandos se han bloqueado debido a **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u>Para solucionar este problema, debe hacer lo siguiente</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) los scripts bloqueados que utilizan `SecureHtmlRenderer` clase.
1. Utilice el `CSPNonceProvider` para permitir la ejecución de scripts.
Adobe Commerce y Magento Open Source 2.4.7 y posteriores incluyen una **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] proveedor para facilitar la generación de [!DNL nonce] cadenas para cada solicitud. Estos [!DNL nonce] a continuación, las cadenas se adjuntan al [!UICONTROL CSP] encabezado.

   Utilice el `generateNonce` función en `Magento\Csp\Helper\CspNonceProvider` para obtener una [!DNL nonce] cadena.

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

1. [añada un [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) al de su módulo `csp_whitelist.xml` archivo.

## Problema: el administrador no puede realizar un pedido

Un administrador no puede enviar una solicitud al administrador **crear página de pedidos**, con el signo &quot;*Se ha rechazado ejecutar un script en línea porque infringe la siguiente directiva de directiva de política de seguridad de contenido: &quot;script-src ...* Mensaje de error &quot; en el registro de la consola del explorador.

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

No es posible enviar una solicitud. Lo siguiente [!DNL JS] El error se muestra en el registro de la consola del explorador: &quot;*Se ha rechazado ejecutar un script en línea porque infringe la siguiente directiva de directiva de política de seguridad de contenido: &quot;script-src ...*&quot;

### Causa

En Adobe Commerce y Magento Open Source versión 2.4.7 y posteriores, **[!UICONTROL CSP]** está configurado en `restrict-mode`, de forma predeterminada, para las páginas de pago de las áreas de tienda y administración, y en `report-only` para todas las demás páginas.
El correspondiente **[!UICONTROL CSP]** el encabezado no contiene `unsafe-inline` palabra clave dentro de `script-src` directiva para páginas de pago. Además, solo [!DNL whitelisted] se permiten scripts en línea.

### Solución

Los usuarios pueden ver errores del explorador debido a que algunas secuencias de comandos se han bloqueado debido a **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u>Para solucionar este problema, debe hacer lo siguiente</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) los scripts bloqueados que utilizan `SecureHtmlRenderer` clase.
1. Utilice el `CSPNonceProvider` para permitir la ejecución de scripts.
Adobe Commerce y Magento Open Source 2.4.7 y posteriores incluyen una **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] proveedor para facilitar la generación de [!DNL nonce] cadenas para cada solicitud. Estos [!DNL nonce] a continuación, las cadenas se adjuntan al [!UICONTROL CSP] encabezado.

   Utilice el `generateNonce` función en `Magento\Csp\Helper\CspNonceProvider` para obtener una [!DNL nonce] cadena.

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

1. [Añadir un [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) al de su módulo `csp_whitelist.xml` archivo.
