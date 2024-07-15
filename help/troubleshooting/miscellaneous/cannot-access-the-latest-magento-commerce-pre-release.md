---
title: No se puede acceder a la última versión preliminar de Adobe Commerce
description: Este artículo proporciona soluciones a problemas que se producen al intentar utilizar el código de versión previa más reciente de Adobe Commerce.
exl-id: cbf54a15-b307-4bfc-90b7-cff98aeb4fce
feature: Roles/Permissions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---

# No se puede acceder a la última versión preliminar de Adobe Commerce

Este artículo proporciona soluciones a problemas que se producen al intentar utilizar el código de versión previa más reciente de Adobe Commerce.

>[!NOTE]
>
>Si tiene problemas con el acceso a Beta, consulte el artículo [No se puede acceder a la última versión de Beta](/help/how-to/general/cannot-access-the-latest-beta-version.md).

## Problema

Este artículo cubre los siguientes problemas con el acceso al código previo al lanzamiento:

* No puede encontrar el código previo al lanzamiento.
* Error al descargar la versión de Adobe Commerce de acceso anticipado desde [magento.com](https://account.magento.com/customer/account/login) mediante Composer.

## Causa

Estas son las causas más comunes de los problemas:

* Está buscando el código de acceso anticipado en la ubicación incorrecta.
* Utiliza un MageID incorrecto al acceder al código a través de Composer.
* Su cuenta no forma parte del programa de prelanzamiento.

## Solución

### Ubicación del código de acceso anticipado

Durante la versión preliminar, los paquetes de versiones están disponibles en dos ubicaciones:

1. A través del Compositor en [magento.com](https://repo.magento.com/), usando el MageID principal de la cuenta. Para obtener más información sobre cómo usar Composer, consulta [Instalar Adobe Commerce con Composer](https://devdocs.magento.com/guides/v2.3/install-gde/composer.html) en nuestra documentación para desarrolladores.
1. **Mi cuenta** > **Descargas** en [account.magento.com](https://account.magento.com/customer/account/login).

>[!NOTE]
>
>Los paquetes de versiones no están disponibles en GitHub hasta la fecha de disponibilidad general.

### ID de imagen que debe utilizar

Debe utilizar el MageID principal asociado a su cuenta de Adobe Commerce o Partner. El programa previo al lanzamiento no está vinculado a ningún contacto que tenga acceso compartido. El acceso anticipado solo se puede obtener a través de Composer o [repo.magento.com](https://repo.magento.com/) mediante el MageID asociado con su licencia de Adobe Commerce o licencia de socio.

#### ¿Cómo averiguo si mi MageID es el principal?

**Para comerciantes**

Para averiguar si el MageID es principal, intente lo siguiente:

1. Inicie sesión en [magento.com](https://account.magento.com/customer/account/login) y vaya a la ficha **Mis productos y servicios**. Compruebe si ve la información de la licencia de Adobe Commerce allí:
   * Si ve la información de licencia de Adobe Commerce, el MageID es el principal.
   * Si no ve la información de licencia de Adobe Commerce, el MageID solo tiene acceso compartido. Para saber quién es el titular del identificador principal, vaya a **Compartido conmigo**. Observe el SHARENAME especificado allí. Haga clic en **Cambiar cuentas** y seleccione el valor que ha anotado en SHARENAME. En la página de bienvenida verá el correo electrónico del titular del ID principal.
1. Si por alguna razón no encuentra esta información en [magento.com](https://account.magento.com/customer/account/login), comuníquese con el equipo de cuenta de Adobe.
1. Si nada de lo anterior funciona, [comuníquese con la atención al cliente](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

**Para socios**

Para averiguar si el MageID es principal, intente lo siguiente:

1. Inicie sesión en [magento.com](https://account.magento.com/customer/account/login) y vaya a la ficha **Mis productos y servicios**. En la subsección Partners, compruebe si ve la información de licencia de Partner activa:
   * Si ve la información de licencia de Partner activa, su MageID es el principal. La licencia de Partner está activa si el valor END DATE es una fecha futura.
   * Si no ve la información de licencia de Partner activa, su MageID solo tiene acceso compartido. Para saber quién es el titular del identificador principal, vaya a **Compartido conmigo**. Observe el SHARENAME especificado allí. Haga clic en **Cambiar cuentas** y seleccione el valor que ha anotado en SHARENAME. En la página de bienvenida verá el correo electrónico del titular del ID principal.
1. Si por algún motivo no encuentra esta información en [magento.com](https://account.magento.com/customer/account/login), comuníquese con su administrador de socios.
1. Si nada de lo anterior funciona, [сcomuníquese con la atención al cliente](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### No forma parte del programa previo al lanzamiento

Para que se incluya en el programa de acceso previo al lanzamiento, su organización debe tener una cuenta de Adobe Commerce o Partner activa que esté al día. Si cree que cumple con este criterio y no puede acceder al código de prelanzamiento, [comuníquese con la atención al cliente](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) con su MageID.
