---
title: Sugerencias de pruebas de terceros para Adobe Commerce en infraestructuras en la nube
description: Este artículo proporciona opciones para compartir el acceso con un tercero para pruebas o validación cuando tenga un problema con una extensión de Adobe Commerce en la infraestructura en la nube.
exl-id: e2d80aa9-8b68-48ed-bec5-68e128611a1e
feature: Best Practices, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# Sugerencias de pruebas de terceros para Adobe Commerce en infraestructuras en la nube

Este artículo proporciona opciones para compartir el acceso con un tercero para pruebas o validación cuando tenga un problema con una extensión de Adobe Commerce en la infraestructura en la nube.
Debe seguir los procedimientos y requisitos de seguridad de datos internos adecuados por su parte a la hora de decidir la forma de proporcionar acceso a terceros.

## Productos y versiones afectados:

* Adobe Commerce en infraestructura en la nube 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.3

## Qué entornos utilizar para realizar pruebas

Según los estándares de seguridad interna, puede elegir que la solución de problemas de terceros se realice en un entorno local. Si el problema no se puede reproducir localmente, es posible que desee proporcionar acceso a su entorno de nube. Si decide hacerlo, asegúrese de trabajar dentro de sus estándares de seguridad interna. Si proporciona acceso a cualquiera de los entornos de nube, asegúrese de que el tercero tenga claro qué se puede hacer y qué aprobación se requiere para cosas como solo replicación o permitir cambios en el código. Esto es especialmente importante para los entornos de producción.

## Proporcionar acceso y datos a terceros

* Proporcione acceso a su proveedor de terceros al entorno de la nube. Artículos relacionados:

   * [Guía del usuario del Centro de ayuda de Adobe Commerce > ACCESO COMPARTIDO: OTORGUE PRIVILEGIOS PARA QUE OTROS USUARIOS TENGAN ACCESO A SU CUENTA](/help/help-center-guide/help-center/magento-help-center-user-guide.md#shared-access) en nuestra base de conocimiento de asistencia.
   * [Compartir tu cuenta de Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/start/commerce-account/commerce-account-share) en nuestra guía de usuario.

* Cree un volcado de la base de datos (o dé acceso al proveedor de terceros para hacerlo). Se puede realizar utilizando la CLI o en el administrador de Commerce. Este volcado de la base de datos ofuscará los datos del cliente, por lo que solo obtendrán el código y los SKU del producto, etc., sin datos de propietario/cliente. Como referencia, usa [Compartir tu cuenta de Commerce] (/help/how-to/general/create-database-dump-on-cloud.md) en nuestra base de conocimiento de asistencia.
* Una vez finalizada la prueba, asegúrese de revocar el acceso compartido a su entorno de nube, tal como se describe en [Guía del usuario del Centro de ayuda de Adobe Commerce > Revocar (eliminar el acceso compartido)](/help/help-center-guide/help-center/magento-help-center-user-guide.md#revoke-shared-access) en nuestra base de conocimiento de asistencia.

## Práctica recomendada de pruebas

La práctica estándar es solucionar problemas en un entorno local. Si el problema no se puede reproducir localmente, vaya a Ensayo. Es posible que el tercero tenga que comprobar la producción. Asegúrese de que el tercero sabe que solo intenta reproducir el problema en producción y ensayo y no realiza ningún cambio en el código. Si necesita hacer cambios en el código, primero debe obtener su permiso.

## Lectura relacionada

* [Prácticas recomendadas para usar extensiones de terceros en Adobe Commerce](https://support.magento.com/hc/en-us/articles/360042361152-Best-Practices-for-using-third-party-extensions-in-Magento) en nuestra base de conocimiento de soporte.
