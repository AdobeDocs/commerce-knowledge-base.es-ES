---
title: Solución de problemas de la página de cierre de tienda en [!UICONTROL CSP] modo restringido
description: Este artículo explica los errores que puede experimentar al ver la página de cierre de compra en modo restringido CSP y proporciona soluciones para corregirlos.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: fb92b75d-c88b-4810-a309-d6ab38485e86
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 0%

---

# Solución de problemas de la página de cierre de tienda en [!UICONTROL CSP] modo restringido

Este artículo proporciona explicaciones y correcciones para los problemas de Adobe Commerce 2.4.7 mientras ve la página de cierre de compra en **[!UICONTROL CSP restricted mode]**, con el signo &quot;*Se ha rechazado ejecutar un script en línea porque infringe la siguiente directiva de directiva de política de seguridad de contenido: &quot;script-src ...* Mensaje de error &quot; en el registro de la consola del explorador.

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube, Adobe Commerce local y Magento Open Source:

* 2.4.7
* 2.4.6-pX
* 2,4,5-pX
* 2.4.4-pX

## Problema: la página de cierre de compra de la tienda está dañada o no se puede cargar

El **pago y envío de tienda** La página está rota o no se puede cargar, con el signo &quot;*Se ha rechazado ejecutar un script en línea porque infringe la siguiente directiva de directiva de política de seguridad de contenido: &quot;script-src ...* Mensaje de error &quot; en el registro de la consola del explorador.

<u>Pasos a seguir</u>:

1. Ve a la tienda.
1. Añada un producto al carro de compras y continúe con el cierre de compra.

<u>Resultados esperados</u>:

La página de cierre de compra se carga completamente normalmente.

<u>Resultados reales</u>:

La página de cierre de compra está en blanco o faltan componentes. Lo siguiente [!DNL JS] El error se muestra en el registro de la consola del explorador: &quot;*Se ha rechazado ejecutar un script en línea porque infringe la siguiente directiva de directiva de política de seguridad de contenido: &quot;script-src ...*&quot;

### Causa

En Adobe Commerce y Magento Open Source versión 2.4.7 y posteriores, **[!UICONTROL CSP]** está configurado en `restrict-mode`, de forma predeterminada, para las páginas de pago de las áreas de tienda y administración, y en `report-only` para todas las demás páginas.
El correspondiente **[!UICONTROL CSP]** el encabezado no contiene `unsafe-inline` palabra clave dentro de `script-src` directiva para páginas de pago. Además, solo [!DNL whitelisted] se permiten scripts en línea.

### Solución

Los usuarios pueden ver errores del explorador debido a que algunas secuencias de comandos se han bloqueado debido a **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

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

Falta la forma de pago o no funciona en el **pago y envío de tienda** página, con el signo &quot;*Se ha rechazado ejecutar un script en línea porque infringe la siguiente directiva de directiva de política de seguridad de contenido: &quot;script-src ...* Mensaje de error &quot; en el registro de la consola del explorador.

<u>Pasos a seguir</u>:

1. Ve a la tienda.
2. Añada un producto al carro de compras y continúe con el cierre de compra.
3. Seleccione una forma de pago.

<u>Resultados esperados</u>:

Puede seleccionar una forma de pago y proceder a realizar un pedido correctamente.

<u>Resultados reales</u>:

Falta la forma de pago o no funciona. Lo siguiente [!DNL JS] El error se muestra en el registro de la consola del explorador: &quot;*Se ha rechazado ejecutar un script en línea porque infringe la siguiente directiva de directiva de política de seguridad de contenido: &quot;script-src ...*&quot;

### Causa

En Adobe Commerce y Magento Open Source versión 2.4.7 y posteriores, **[!UICONTROL CSP]** está configurado en `restrict-mode`, de forma predeterminada, para las páginas de pago de las áreas de tienda y administración, y en `report-only` para todas las demás páginas.
El correspondiente **[!UICONTROL CSP]** el encabezado no contiene `unsafe-inline` palabra clave dentro de `script-src` directiva para páginas de pago. Además, solo [!DNL whitelisted] se permiten scripts en línea.

### Solución

Los usuarios pueden ver errores del explorador debido a que algunas secuencias de comandos se han bloqueado debido a **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

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

## Problema: el cliente no puede realizar un pedido

Un cliente no puede realizar un pedido con el signo &quot;*Se ha rechazado ejecutar un script en línea porque infringe la siguiente directiva de directiva de política de seguridad de contenido: &quot;script-src ...* Mensaje de error &quot; en el registro de la consola del explorador.

<u>Pasos a seguir</u>:

1. Ve a la tienda.
2. Añada un producto al carro de compras y continúe con el cierre de compra.
3. Seleccione una forma de pago.
4. Clic **Realizar pedido**.

<u>Resultados esperados</u>:

Puede realizar un pedido con éxito.

<u>Resultados reales</u>:

No eres capaz de hacer un pedido. Lo siguiente [!DNL JS] El error se muestra en el registro de la consola del explorador: &quot;*Se ha rechazado ejecutar un script en línea porque infringe la siguiente directiva de directiva de política de seguridad de contenido: &quot;script-src ...*&quot;

### Causa

En Adobe Commerce y Magento Open Source versión 2.4.7 y posteriores, **[!UICONTROL CSP]** está configurado en `restrict-mode`, de forma predeterminada, para las páginas de pago de las áreas de tienda y administración, y en `report-only` para todas las demás páginas.
El correspondiente **[!UICONTROL CSP]** el encabezado no contiene `unsafe-inline` palabra clave dentro de `script-src` directiva para páginas de pago. Además, solo [!DNL whitelisted] se permiten scripts en línea.

### Solución

Los usuarios pueden ver errores del explorador debido a que algunas secuencias de comandos se han bloqueado debido a **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

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
