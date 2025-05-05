---
title: Solucionar problemas del módulo [!UICONTROL Product Recommendations] en Adobe Commerce
description: Este artículo trata sobre sugerencias de solución de problemas para el módulo [!UICONTROL Product Recommendations] en Adobe Commerce.
exl-id: 431ee31e-eb5b-400c-9c99-cc86613453d7
feature: Cache, Compliance, Extensions, Marketing Tools, Personalization, Products, Recommendations
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# Solucionar problemas del módulo [!UICONTROL Product Recommendations] en Adobe Commerce

Este artículo trata sobre sugerencias de solución de problemas para

```php
magento/product-recommendations
```

módulo y su dependencia

```php
saas-export
```

ya que necesita que ambos módulos funcionen para poder usar la herramienta [!UICONTROL Product Recommendations] en Adobe Commerce.

## Productos y versiones afectados

* Adobe Commerce 2.4.4: 2.4.7

## Solucionar problemas del módulo de recomendaciones de productos

Si ha configurado la variable

```php
magento/product-recommendations
```

módulo correctamente, (Compruebe [[!UICONTROL Product Recommendations - Install and Configure]](https://experienceleague.adobe.com/es/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure) en nuestra documentación para desarrolladores). pero no está viendo ninguna recomendación, intente lo siguiente:

* Es posible que el módulo no haya tenido tiempo suficiente para recopilar datos de comportamiento. Permita que el sistema funcione durante 24 horas para que pueda empezar a recopilar datos. Considere implementar un tipo de recomendación que no requiera datos de comportamiento, como &quot;*Más como esto*&quot;.

* Si no ve las recomendaciones que ha configurado, es posible que aún no haya datos suficientes para crear recomendaciones para el usuario.

* Asegúrese de que el espacio de datos [!DNL SaaS] o la clave [!DNL API] sean válidos. Si aparece un error después de especificar el espacio de datos [!DNL SaaS] o la clave [!DNL API] durante la inicialización de las recomendaciones del producto, compruebe que ha escrito correctamente el espacio de datos [[!DNL SaaS] y la clave [!DNL API] key](https://experienceleague.adobe.com/es/docs/commerce-admin/config/services/saas) (en nuestra guía del usuario). Para asegurarse de que las claves [!DNL MageID] y [!DNL API] estén vinculadas, el usuario propietario de [!DNL MageID], que suele ser el propietario de la licencia de Adobe Commerce, debe ser el mismo usuario que genera la clave [!DNL API]. Si debe cambiar el [!DNL MageID] que se utilizó, [envíe un vale de soporte técnico](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

>[!NOTE]
>
>Si [**[!UICONTROL Cookie Restriction Mode]**](https://experienceleague.adobe.com/es/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law) (en nuestra guía del usuario) está *habilitado*, Adobe Commerce no recopila datos de comportamiento hasta que el comprador da su consentimiento. Si **[!UICONTROL Cookie Restriction Mode]**&#x200B;está *deshabilitado*, Adobe Commerce recopila datos de comportamiento de forma predeterminada.

## Módulo de exportación del catálogo [!DNL SaaS]

Para problemas relacionados con la exportación del catálogo [!DNL SaaS] (

```php
saas-export
```

) módulo:

1. Confirme que se están ejecutando los trabajos [[!DNL cron]](https://experienceleague.adobe.com/es/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) (en nuestra documentación para desarrolladores).
1. Confirme que [[!UICONTROL indexers]](https://experienceleague.adobe.com/es/docs/commerce-operations/configuration-guide/cli/manage-indexers) (en nuestra documentación para desarrolladores) se están ejecutando y el    ```php    Product Feed    ```    [!UICONTROL indexer] está establecido en    ```php    Update by Schedule    ```    .
1. Confirme que los módulos están *habilitados*. El    ```php    saas-export    ```    metapackage instala los siguientes módulos, todos los cuales deben estar *habilitados*:    ```php    "magento/module-catalog-data-exporter"      "magento/module-catalog-inventory-data-exporter"      "magento/module-catalog-url-rewrite-data-exporter"      "magento/module-configurable-product-data-exporter"      "magento/module-data-exporter"      "magento/module-saas-catalog"    ```
1. Compruebe los [registros](https://experienceleague.adobe.com/es/docs/commerce-operations/configuration-guide/cli/enable-logging) (en nuestra documentación para desarrolladores). Asegúrese de que no haya errores asociados con los módulos anteriores.
1. Actualice [!UICONTROL Configuration cache]. Vaya a **Sistema** > **Herramientas** > **Administración de caché** y borre [!UICONTROL Configuration cache].
1. Confirme que hay datos en la tabla de base de datos `cde_products_products_feed`.

   >[!NOTE]
   >
   >Si no encuentra esa tabla, compruebe la tabla `catalog_data_exporter_products`. El nombre de la tabla se cambió en la versión 103.3.0 de [!DNL Data Export].

## Eventos

[Verificar la colección de eventos](https://experienceleague.adobe.com/es/docs/commerce-merchant-services/product-recommendations/getting-started/verify), en nuestra documentación para desarrolladores, describe los eventos de comportamiento que se envían a Adobe Commerce.

## Lectura relacionada

* [Desarrollo del administrador de Recommendations del producto](https://experienceleague.adobe.com/es/docs/commerce-merchant-services/product-recommendations/developer/development-overview) en nuestra documentación para desarrolladores
* [Introducción a Product Recommendations](https://experienceleague.adobe.com/es/docs/commerce-merchant-services/product-recommendations/overview) en la Guía de Product Recommendations
* [Crear Recommendations de producto](https://experienceleague.adobe.com/es/docs/commerce-merchant-services/product-recommendations/admin/create) en la Guía de Recommendations de productos
* [Revisar registros y solucionar problemas](https://experienceleague.adobe.com/es/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging) en la Guía de exportación de datos de [!DNL SaaS]
* [[!DNL SaaS] Notas de la versión de Data Export Extension](https://experienceleague.adobe.com/es/docs/commerce-merchant-services/saas-data-export/release-notes) en la Guía de exportación de datos de Adobe Commerce para [!DNL SaaS] servicios
* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/es/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce

