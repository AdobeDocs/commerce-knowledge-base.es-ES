---
title: No se puede acceder a la última versión de Beta
description: Este artículo proporciona soluciones a problemas que se producen al intentar utilizar las últimas versiones de código de Beta para Adobe Commerce. El código Beta solo está disponible para socios de Adobe oficiales que hayan seguido el proceso descrito en [Programa Adobe Commerce Beta](https://github.com/magento/magento2/wiki/Magento-Beta-Program).
exl-id: a53c854e-38a8-4c8c-8586-9d99c576c835
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# No se puede acceder a la última versión de Beta

Este artículo proporciona soluciones a problemas que se producen al intentar utilizar las últimas versiones de código de Beta para Adobe Commerce. El código Beta solo está disponible para los socios de Adobe oficiales que hayan seguido el proceso descrito en [Programa Adobe Commerce Beta](https://github.com/magento/magento2/wiki/Magento-Beta-Program).

## Problema

Este artículo cubre los siguientes problemas con el acceso al código de acceso anticipado:

* La versión de Adobe Commerce Beta no se puede descargar en **Mi cuenta** > **Descargas** en [magento.com](https://account.magento.com/customer/account/login).
* Error al descargar la versión de Adobe Commerce de acceso anticipado desde [magento.com](https://account.magento.com/customer/account/login) mediante Composer.

## Causa

Estas son las causas más comunes de los problemas:

* Está buscando el código de acceso anticipado en la ubicación incorrecta.
* Está utilizando un MageID incorrecto.
* El desarrollador necesita claves de acceso desde el MageID correcto.
* Su cuenta no forma parte del programa Beta.

## Solución

### Ubicación del código de acceso anticipado

Durante los períodos de acceso a la versión beta, los paquetes de la versión solo están disponibles a través de Composer en [repo.magento.com](https://repo.magento.com/). Los paquetes de versiones no están disponibles en los portales de GitHub y Adobe Commerce durante este periodo y los publicaremos en estas ubicaciones en la fecha de GA. Para obtener más información sobre cómo usar Composer, haga clic [aquí](https://devdocs.magento.com/guides/v2.3/install-gde/composer.html).

### ID de imagen que debe utilizar

Debe utilizar el MageID principal asociado a su cuenta de Partner. El programa Beta no está vinculado a ningún contacto que tenga acceso compartido. Solo se puede acceder al acceso anticipado a través de Composer o [repo.magento.com](https://repo.magento.com/) mediante el MageID asociado con su licencia de socio.

#### ¿Cómo puedo averiguar si mi MageID es el principal?

Para averiguar si el MageID es principal, intente lo siguiente:

1. Inicie sesión en [magento.com](https://account.magento.com/customer/account/login) y vaya a la ficha **Mis productos y servicios**. En la subsección Partners, compruebe si ve la información de licencia de Partner activa:
   * Si ve la información de licencia de Partner activa, su MageID es el principal. La licencia de Partner está activa si el valor END DATE es una fecha futura.
   * Si no ve la información de licencia de Partner activa, su MageID solo tiene acceso compartido. Para saber quién es el titular del identificador principal, vaya a **Compartido conmigo**. Observe el SHARENAME especificado allí. Haga clic en **Cambiar cuentas** y seleccione el valor que ha anotado en SHARENAME. En la página de bienvenida, verá el correo electrónico del titular del ID principal.
1. Si por algún motivo no encuentra esta información en [magento.com](https://account.magento.com/customer/account/login), comuníquese con su administrador de socios.
1. Si nada de lo anterior funciona, [comuníquese con la atención al cliente](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed).

#### El desarrollador no tiene acceso correcto a las claves

Si usted es el propietario principal de MageID y necesita dar acceso a un desarrollador de su equipo, siga los siguientes pasos:

1. Haga que el propietario principal de MageID inicie sesión en [account.magento.com](https://account.magento.com/customer/account/login).
1. Seleccione la ficha **Marketplace** y, a continuación, haga clic en **Claves de acceso**.
1. Seleccione **Crear una nueva clave de acceso** y asígnele un nombre.
1. Envíe las claves a su desarrollador.

### No es parte del programa de acceso anticipado

Nuestro programa Beta Access solo está disponible para nuestros socios técnicos y de soluciones, de modo que puedan evaluar nuestro código de preproducción. Para que se incluya en el programa Beta Access, su organización debe tener una cuenta de socio de Adobe activa que esté al día y haber firmado el NDA de Beta [aquí](https://github.com/magento/magento2/wiki/Magento-Beta-Program). Si cree que cumple estos criterios y no puede acceder al código beta, póngase en contacto con [commercebeta@adobe.com](mailto:commercebeta@adobe.com).
