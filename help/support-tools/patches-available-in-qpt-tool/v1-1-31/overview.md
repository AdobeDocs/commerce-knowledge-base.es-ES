---
title: 'Información general: [!DNL Quality Patches Tool] (QPT) v1.1.31'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.31.
exl-id: 0d93619e-0ae6-4dba-9b76-8aeb026c456d
feature: Tools and External Services
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.31

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.31.

QPT v1.1.31 incluye los siguientes parches:

1. **ACSD-50817**: Optimiza el trabajo cron `sales_clean_quotes` para ejecutarse más rápido añadiendo un índice compuesto en `store_id` y `updated_at` columnas de la tabla de comillas.
1. **ACSD-50345**: soluciona el problema donde: [!DNL Google reCAPTCHA v2] no se vuelve a cargar después de enviar un pago fallido, [!DNL Google reCAPTCHA v3 Invisible] no funciona en el cierre de compra y no se puede realizar el pedido, y [!UICONTROL PlaceOrder] evento no activado.
1. **ACSD-49392**: corrige el problema en el que el estado del pedido cambia a cerrado después de un reembolso parcial de un producto agrupado.
1. **ACSD-51036**: corrige el problema en el cual las condiciones de carrera durante las llamadas simultáneas a la API de REST dan como resultado una sobrescritura de la información de estado de envío en la [!UICONTROL Items Ordered] tabla.
1. **ACSD-50858**: Corrige la emisión en la que un cupón se marca incorrectamente como utilizado después de un pago con tarjeta fallido.

Utilice el menú de la izquierda para navegar a una página específica del parche.
