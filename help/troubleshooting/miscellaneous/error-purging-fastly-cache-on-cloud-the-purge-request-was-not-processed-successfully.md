---
title: Error al purgar la caché de Fastly en la nube (la solicitud de purga no se procesó correctamente)
description: '''Este artículo proporciona una corrección para cuando utiliza una opción de purga de Fastly y recibe el error: *La solicitud de purga no se procesó correctamente*. Fastly es un servicio de CDN y almacenamiento en caché incluido con Adobe Commerce en planes e implementaciones de infraestructura en la nube. Si intenta utilizar una opción de depuración de Fastly y no se procesa, es posible que tenga credenciales de Fastly incorrectas en el entorno o que se haya encontrado un problema."'
exl-id: 568b1f4c-2ccb-4740-a6e4-d227a55fcfe6
feature: Cache, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# Error al purgar la caché de Fastly en la nube (la solicitud de purga no se procesó correctamente)

Este artículo proporciona una corrección para cuando utiliza una opción de depuración de Fastly y recibe el error: *La solicitud de purga no se ha procesado correctamente*. Fastly es un servicio de CDN y almacenamiento en caché incluido con Adobe Commerce en planes e implementaciones de infraestructura en la nube. Si intenta utilizar una opción de depuración de Fastly y no se procesa, es posible que tenga credenciales de Fastly incorrectas en el entorno o que se haya encontrado un problema.

Esta información le ayuda a verificar y probar los encabezados de Fastly para su sitio activo y servidores de origen.

## Versiones afectadas

* Adobe Commerce en la infraestructura en la nube 2.1.X y posterior
* Fastly 1.2.27 y posterior

## Problema

El almacenamiento en caché funciona, pero cuando intenta purgar, recibe un error o no funciona. El error incluye: &quot;La solicitud de purga no se procesó correctamente&quot;.

## Causa

Es posible que tenga credenciales incorrectas establecidas en el entorno o que necesite cargar fragmentos de VCL.

## Resolver

### Comprobar credenciales de Fastly

Compruebe si tiene el ID de servicio rápido y el token de API correctos en su entorno. Si tiene credenciales de ensayo en producción, es posible que las depuraciones no se procesen o procesen incorrectamente.

1. Inicie sesión en el administrador local de Commerce como administrador.
1. Clic **Tiendas** > Configuración > **Configuración** > **Avanzadas** > **Sistema** y ampliar **Caché de página completa**.    ![magento_full_page_cache_2.4.1.png](assets/magento_full_page_cache_2.4.1.png)
1. Expanda Configuración de Fastly y verifique el ID de servicio de Fastly y el token de API para su entorno.
1. Si modifica los valores, haga clic en Credenciales de prueba.

### Compruebe los fragmentos de VCL

Si las credenciales son correctas, es posible que tenga problemas con sus VCL. Para enumerar y revisar las VCL por servicio, introduzca la siguiente llamada de API en un terminal:

```
curl -X GET -s https://api.fastly.com/service/<Service ID>/version/<Editable Version #>/snippet -H "Fastly-Key:FASTLY_API_TOKEN"
```

Revise la lista de VCL. Si tiene problemas con las VCL predeterminadas de Fastly, puede volver a cargar o verificar el contenido según el [VCL predeterminados rápidos](https://github.com/fastly/fastly-magento2/tree/master/etc/vcl_snippets). Para editar sus VCL personalizados, consulte [Fragmentos de VCL personalizados de Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html) en la Guía de infraestructura de Commerce en la nube.

## Más información

En nuestra documentación para desarrolladores:

* [Acerca de Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)
* [Configuración rápida](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)
* [Fragmentos de VCL personalizados de Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html)
