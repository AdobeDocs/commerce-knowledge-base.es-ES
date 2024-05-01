---
title: 'Información general: [!DNL Quality Patches Tool] (QPT) v1.1.33'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.33.
feature: Tools and External Services
role: Admin
exl-id: df3ae5e2-7c57-4ccd-af34-eb78cc60bcf6
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.33

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.33.

QPT v1.1.33 incluye los siguientes parches:

1. **ACSD-50478**: corrige el comando de reversión de la base de datos para un caso en el que el volcado de la base de datos contiene déclencheur y un comando SQL delimitador.
1. **ACSD-50512**: corrige el error: *El vínculo descargable no está relacionado con el producto. Compruebe el vínculo e inténtelo de nuevo.*  esto sucede al actualizar la fecha de inicio de una actualización de ensayo de producto descargable.
1. **ACSD-50949**: corrige el problema en el que el filtro de precio de [!UICONTROL Advanced Search] no devuelve los resultados adecuados cuando se utiliza junto con el filtro SKU.
1. **ACSD-51645**: corrige el error producido al guardar un nuevo [!UICONTROL Cart Price Rule] si la extensión `Magento_OfflineShipping` está deshabilitada.
1. **ACSD-50895**: soluciona el problema donde [!DNL Google Analytics] 3 Las etiquetas GTM no se activan si [!DNL Google Analytics] 4 La GTM no está configurada.
1. **ACSD-51102**: corrige el problema en el que una regla de catálogo aplicada a un gran número de productos no se indexa correctamente cuando la regla se activa mediante una actualización programada.
1. **ACSD-50368**: corrige el problema en el que el `group_id` se ignora cuando se crea un cliente mediante la API de REST asíncrona o la API de REST asíncrona masiva.
1. **ACSD-51497**: corrige un problema en el cual un cliente no puede ordenar una página de catálogo por [!UICONTROL Custom Attribute] del tipo desplegable.
1. **ACSD-51408**: corrige el problema en el que el estado del elemento de pedido se establece incorrectamente como [!UICONTROL Backordered].
1. **ACSD-51735**: corrige el problema en el que el estado del elemento de pedido se establece incorrectamente como [!UICONTROL Ordered] cuando el stock de productos es *0*.
1. **ACSD-51792**: corrige el problema en el que una página no tiene el evento de impresión cuando [!DNL Google Tag Manager] 4 está activada.
1. **ACSD-51471**: corrige el problema en el cual un usuario administrador no puede guardar una actualización programada para un producto agrupado que utiliza un producto simple que tiene una actualización programada.
1. **ACSD-51700**: corrige el error que se produce al cambiar de vista de tienda en una página de edición de producto descargable en el administrador.
1. **ACSD-51120**: corrige el problema en el que la caché de solicitudes de GET de GraphQL no se borra para las páginas de CMS que contienen bloques de CMS que se actualizan mediante una actualización de ensayo.
1. **ACSD-51240**: corrige el problema en el que falta el archivo cargado si el registro se realiza mediante el formulario de registro de empresa.
1. **ACSD-51907**: corrige el problema en el cual un usuario administrador restringido no puede crear una nota de crédito con un reembolso sin conexión.
1. **ACSD-52148**: corrige el problema en el que las variables [!UICONTROL Google V3 reCAPTCHA Admin] el inicio de sesión falla ocasionalmente.
1. **ACSD-51431**: corrige el problema en el que un estado de indexador funciona aunque no haya entradas nuevas en el registro de cambios.
1. **ACSD-51892**: corrige el problema de rendimiento en el que los archivos de configuración se cargan varias veces durante la implementación.

Utilice el menú de la izquierda para navegar a una página específica del parche.
