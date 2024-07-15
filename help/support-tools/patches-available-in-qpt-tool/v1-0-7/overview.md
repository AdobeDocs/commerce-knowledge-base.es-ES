---
title: "Información general:  [!DNL Quality Patches Tool] (QPT) v1.0.7"
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.0.7.
exl-id: 2415ca7a-4aec-4a63-9ae9-ee7b29bbc8d7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# Información general de [!DNL Quality Patches Tool] (QPT) v1.0.7

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.0.7.

QPT v1.0.7 incluye los siguientes parches:

1. **MDVA-29148**: corrige el problema que se producía al crear un producto a través de una llamada de API; el tipo de atributo personalizado de producto de `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (como Multiselect) no usa su valor predeterminado si no se proporcionó ningún valor en la carga.
1. **MDVA-29389**: corrige el problema con los informes avanzados donde el cronjob `analytics_collect_data` indica: *El puerto debe configurarse en el parámetro de host (como localhost:3306)*.
1. **MDVA-30594**: corrige el problema en el cual un pedido con varias direcciones no se podía guardar durante la desprotección cuando se configuraba FTP.
1. **MDVA-30782**: corrige el problema en el que el bloque dinámico se muestra independientemente de la regla del carro de compras.
1. **MDVA-30815**: corrige el problema que se producía al cambiar la cantidad de resultados de búsqueda que deben mostrarse en la página de resultados de búsqueda.
1. **MDVA-30837**: Agrega opciones de configuración para el cálculo del envío gratuito, de modo que el usuario pueda configurar la cantidad mínima del pedido para obtener el envío gratuito según el subtotal (o el total general).
1. **MDVA-30945**: corrige el problema por el que se recibe un mensaje de error grave al actualizar los carros de compras `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.
1. **MDVA-30972**: corrige el problema en el cual el estado del pedido personalizado se cambió a *Procesando* después de la creación parcial del envío mediante WebApi.
1. **MDVA-31007**: corrige el problema en el cual los atributos de dirección personalizados no se muestran correctamente en la página de detalles del pedido en el área de mi cuenta y en el servidor.
1. **MDVA-31021**: corrige el problema donde existen problemas de rendimiento en `module-catalog-import-export/Model/Import/Product/Option.php`. Si hay más de ~100k registros en la tabla `catalog_product_option`, un nuevo CSV con un solo producto tarda menos de 10 segundos en validarse.
1. **MDVA-31224**: Mejora el rendimiento de la operación de reindexación `catalog_product_price` para los productos agrupados.
1. **MDVA-31282**: corrige el problema en el que ocurren autorizaciones dobles en [!DNL Paypal PayFlow Pro] en Adobe Commerce. Las autorizaciones dobles también tienen el efecto de omitir [!DNL PayFlow Pro's] filtros de fraude y duplicar las tarifas de transacción.
1. **MDVA-31343**: corrige el problema con la clase de cuerpo `page-layout-category-full-width` eliminada cuando se programa una categoría.

Utilice el menú de la izquierda para navegar a una página específica del parche.
