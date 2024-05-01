---
title: "ACSD-50858: rendimiento mejorado para cargar el contenido de los titulares"
description: Aplique el parche ACSD-50858 para corregir el problema de Adobe Commerce en el que el rendimiento del banner se ve afectado en la página del carro de compras/cierre de compra debido a consultas de base de datos excesivas y a un mayor tiempo de carga de la página.
exl-id: f9526d66-fc0e-44a0-8c72-b9f183004840
feature: Page Content
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# ACSD-50858: rendimiento mejorado para cargar contenido de titulares

El parche ACSD-50858 corrige un problema de rendimiento del banner en la página de carrito/cierre de compra: *consultas de BD excesivas y tiempo de carga de la página aumentado*. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.31 está instalado. El ID del parche es ACSD-50858. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El rendimiento del titular se ve afectado en la página del carro de compras/cierre de compra debido a *consultas de BD excesivas y tiempo de carga de la página aumentado*.

Esto se solucionó refactorizando la forma en que se cargan los contenidos de los banners, lo que redujo el número de consultas de DB en un 99,99 % y el tiempo de carga de la página en ~99 %.

<u>Pasos a seguir</u>:

1. Inicie sesión en Admin y cree un producto sencillo.
1. Cree un cliente, ya sea desde Administración o desde el front-end, y añada una dirección de envío para él.
1. Mueva banners.php a `magento_root/pub/` carpeta.
1. Generar titulares utilizando  `php pub/banners.php` comando. Generará 10.000 banners simples y 1.000 banners con reglas de venta.
1. Inicie sesión en el cliente creado anteriormente en el front-end.
1. Añadir el producto creado anteriormente al carro de compras.
1. Vaya a la página de cierre de compra (cierre de compra/carro).
1. Monitorización de `banner/ajax/load` tiempo de carga de la solicitud:

   * Sin `bin/magento dev:query-log:enable`
   * Con `bin/magento dev:query-log:enable`

     ```
     grep 'magento_banner_content' var/debug/db.log  | wc -l
     ```

<u>Resultados esperados</u>:

Disminución del número de consultas de BD para `magento_banner_content` y tiempo de carga de la página de carro/cierre de compra.

<u>Resultados reales</u>:

Aumento en el número de consultas de BD para `magento_banner_content` y tiempo de carga de la página de carro/cierre de compra.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Información adicional

<u>contenido de banners.php</u>:

```php
\Banner::class);
    $banner->setIsEnabled(
        \Magento\Banner\Model\Banner::STATUS_ENABLED
    )->setName(
        'Test Dynamic Block '.$i
    )->setTypes(
        ''
    )->setStoreContents(
        [0 => 'Dynamic Block Content '.$i]
    )->save();
}

$objectManager = \Magento\Framework\App\ObjectManager::getInstance();

/** @var \Magento\SalesRule\Model\Rule $salesRule */
$salesRule = $objectManager->create(\Magento\SalesRule\Model\Rule::class);
$salesRule->setData(
    [
        'name' => '50% Off ',
        'is_active' => 1,
        'customer_group_ids' => [\Magento\Customer\Model\GroupManagement::NOT_LOGGED_IN_ID],
        'coupon_type' => \Magento\SalesRule\Model\Rule::COUPON_TYPE_NO_COUPON,
        'conditions' => [
            [
                'type' => \Magento\SalesRule\Model\Rule\Condition\Address::class,
                'attribute' => 'base_subtotal',
                'operator' => '>',
                'value' => 0
            ]
        ],
        'simple_action' => 'by_percent',
        'discount_amount' => 50,
        'discount_step' => 0,
        'stop_rules_processing' => 1,
        'website_ids' => [
           1
        ]
    ]
);
$salesRule->save();

for ($i = 0; $i < 1000; $i++) {

    $banner = $objectManager->create(\Magento\Banner\Model\Banner::class);
    $banner->setData(
        [
            'name' => 'Get 50% Off ',
            'is_enabled' => \Magento\Banner\Model\Banner::STATUS_ENABLED,
            'types' => [], /*Any Banner Type*/
            'store_contents' => ['<img src="http://example.com/banner_40_percent_off.png" />'],
            'banner_sales_rules' => [$salesRule->getId()],
        ]
    );
    $banner->save();
}
```

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
