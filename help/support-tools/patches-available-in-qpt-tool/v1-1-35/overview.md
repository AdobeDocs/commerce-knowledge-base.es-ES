---
title: 'Información general: [!DNL Quality Patches Tool] (QPT) v1.1.35'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.35.
feature: Tools and External Services
role: Admin
exl-id: 46228690-44ce-462f-b700-1aea6fa0eeab
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.35

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.35.

QPT v1.1.35 incluye los siguientes parches:

1. **ACSD-51899**: corrige el problema en el cual la dirección de envío predeterminada en el paso de envío de cierre de compra se rellena automáticamente con una dirección de recogida en tienda seleccionada anteriormente.
1. **ACSD-52041**: corrige el problema en el que el mensaje de error: *[ERROR] [!DNL Page Builder] se ha procesado durante 5 segundos sin liberar bloqueos*. aparece en [!DNL Chrome] al guardar contenido editado con [!DNL Page Builder].
1. **ACSD-52095**: corrige el problema en el que las variables `manage_stock` el valor se ha definido incorrectamente como 0 en el archivo CSV después de la exportación del producto.
1. **ACSD-51358**: corrige un problema en el cual al eliminar una actualización programada sin una fecha de finalización se eliminan otras actualizaciones programadas para la misma entidad.
1. **ACSD-48070**: corrige el problema en el que la edición de una actualización programada déclencheur una excepción.
1. **ACSD-51890**: corrige el problema en el que las variables [!UICONTROL Submit review] se puede hacer clic varias veces sin [!DNL Google] Validación de reCAPTCHA v3.
1. **ACSD-51984**: corrige el problema donde no está marcado *Usar valor predeterminado y valores de campo de producto no predeterminados* no se guardan para el segundo sitio web, tienda y vista de tienda.
1. **ACSD-52398**: corrige el error *La cantidad solicitada no está disponible* que se produce al intentar actualizar la cantidad de un producto agrupado en el carro de compras de la tienda.
1. **ACSD-52786**: corrige el problema en el que se aplica un SKU de condición de regla de catálogo a todos los productos que comienzan con el SKU determinado.
1. **ACSD-52921**: corrige el problema en el que se produce un error interno al solicitar los detalles del carro de compras a GraphQL cuando hay un producto configurable sin existencias en el carro de compras.
1. **ACSD-51683**: corrige el problema en el cual una opción personalizable no se puede agregar al carro de compras mediante GraphQL.
1. **ACSD-52133**: corrige el problema en el cual una cuenta de cliente no se puede guardar después de una actualización.
1. **ACSD-52202**: corrige el problema en el que la cantidad escalable de stock predeterminado cambia incorrectamente a 0 cuando se cambia un stock no predeterminado a 0 qty en el cumplimiento del pedido.
1. **ACSD-51265**: soluciona el problema con `catalog_product_price` rendimiento de reindexación cuando hay demasiados productos agrupados en el sistema.
1. **ACSD-52831**: corrige el problema en el que los clientes no pueden realizar pedidos de presupuesto negociables cuando [!DNL Google reCAPTCHA v3 Invisible] está activada.
1. **ACSD-51845**: corrige el problema en el cual los productos subsiguientes con precios de nivel y diferentes conjuntos de atributos no se pueden actualizar a través de la API de REST masiva asíncrona.
1. **ACSD-52815**: corrige el problema en el que la entrada del campo de cantidad de un origen no predeterminado solo admite hasta 6 dígitos, a diferencia de 8 para un stock predeterminado.
1. **ACSD-51149**: soluciona el problema donde [!UICONTROL Scheduled ImportExport] con habilitado [!UICONTROL Catalog Permissions] invalida los indexadores y luego los vaciados de caché de cron.
1. **ACSD-50815**: corrige el problema en el que la cantidad decimal de un producto simple no se puede utilizar para una nueva opción de producto agrupado.
1. **ACSD-52399**: corrige el problema en el que se muestra la opción de producto configurable con una cantidad comercializable de 0 *En stock* en la página de producto.

Utilice el menú de la izquierda para navegar a una página específica del parche.
