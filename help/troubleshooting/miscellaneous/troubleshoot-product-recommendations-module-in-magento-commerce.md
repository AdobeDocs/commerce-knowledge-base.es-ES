---
title: Solucionar problemas del módulo Product Recommendations en Adobe Commerce
description: Este artículo trata sobre sugerencias de solución de problemas para
exl-id: 431ee31e-eb5b-400c-9c99-cc86613453d7
feature: Cache, Compliance, Extensions, Marketing Tools, Personalization, Products, Recommendations
role: Developer
source-git-commit: b20ad74194bacb09116131f4a8da1006da75738a
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Solucionar problemas del módulo Product Recommendations en Adobe Commerce

Este artículo trata sobre sugerencias de solución de problemas para

```php
magento/product-recommendations
```

módulo y su dependencia

```php
saas-export
```

ya que necesita que ambos módulos funcionen para utilizar la herramienta Product Recommendations en Adobe Commerce.

## Productos y versiones afectados

* Adobe Commerce 2.4.4: 2.4.7

## Solucionar problemas del módulo de recomendaciones de productos

Si ha configurado la variable

```php
magento/product-recommendations
```

módulo correctamente (Marque [Recommendations de productos: instalación y configuración de Recommendations](https://devdocs.magento.com/recommendations/install-configure.html) en nuestra documentación para desarrolladores ), pero no está viendo ninguna recomendación, intente lo siguiente:

* Es posible que el módulo no haya tenido tiempo suficiente para recopilar datos de comportamiento. Permita que el sistema funcione durante 24 horas para que pueda empezar a recopilar datos. Considere implementar un tipo de recomendación que no requiera datos de comportamiento, como &quot;Más como esto&quot;.

* Si no ve las recomendaciones que ha configurado, es posible que aún no haya datos suficientes para crear recomendaciones para el usuario.

* Asegúrese de que el espacio de datos SaaS o la clave de API sean válidos. Si se produce un error después de especificar el espacio de datos SaaS o la clave de API durante la inicialización de las recomendaciones del producto, asegúrese de haber introducido el [Espacio de datos SaaS y clave de API](https://docs.magento.com/user-guide/configuration/services/saas.html) (en nuestra guía del usuario) correctamente. Para garantizar que MageID y la clave de API estén vinculados, el usuario propietario del MageID, normalmente el usuario propietario de la licencia de Adobe Commerce, debe ser el mismo usuario que genere la clave de API. Si debe cambiar el MageID que ha utilizado, [enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

>[!NOTE]
>
>If [Modo de restricción de cookies](https://docs.magento.com/m2/ce/user_guide/stores/compliance-cookie-restriction-mode.html) (en nuestra guía del usuario) está activada, Adobe Commerce no recopila datos de comportamiento hasta que el comprador da su consentimiento. Si el modo de restricción de cookies está deshabilitado, Adobe Commerce recopila datos de comportamiento de forma predeterminada.

## Módulo de exportación de SaaS de catálogo

Para problemas relacionados con la exportación de SaaS de catálogo (

```php
saas-export
```

) módulo:

1. Confirme el [cron](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-cron.html) (en nuestra documentación para desarrolladores) se están ejecutando trabajos.
1. Confirme el [indexadores](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html) (en nuestra documentación para desarrolladores) están en ejecución y el    ```php    Product Feed    ```    el indexador se ha establecido en    ```php    Update by Schedule    ```    .
1. Confirme que los módulos están activados. El    ```php    saas-export    ```    metapackage instala los siguientes módulos, todos los cuales deben estar habilitados:    ```php    "magento/module-catalog-data-exporter"      "magento/module-catalog-inventory-data-exporter"      "magento/module-catalog-url-rewrite-data-exporter"      "magento/module-configurable-product-data-exporter"      "magento/module-data-exporter"      "magento/module-saas-catalog"    ```
1. Compruebe la [registros](https://devdocs.magento.com/guides/v2.3/config-guide/cli/logging.html) (en nuestra documentación para desarrolladores). Asegúrese de que no haya errores asociados con los módulos anteriores.
1. Actualice la caché de configuración. Ir a **Sistema** > **Herramientas** > **Administración de caché** y borre la caché de configuración.
1. Confirme que hay datos en el    ```php    catalog_data_exporter_products    ```    tabla de base de datos.

## Eventos

[Eventos de recomendación](https://devdocs.magento.com/recommendations/verify.html), en nuestra documentación para desarrolladores, describe los eventos de comportamiento que se envían a Adobe Commerce.

## Lectura relacionada

* [Recommendations de productos: información general](https://devdocs.magento.com/recommendations/product-recs.html) en nuestra documentación para desarrolladores
* [Recommendations de productos: instalación y configuración de Recommendations](https://devdocs.magento.com/recommendations/install-configure.html) en nuestra documentación para desarrolladores
* [Marketing: Recommendations de producto](https://docs.magento.com/m2/ee/user_guide/marketing/product-recommendations.html) en nuestra guía del usuario
* [Crear Recommendations del producto](https://docs.magento.com/m2/ee/user_guide/marketing/create-new-rec.html) en nuestra guía del usuario
