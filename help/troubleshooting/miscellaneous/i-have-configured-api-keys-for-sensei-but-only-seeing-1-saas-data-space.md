---
title: No se pueden ver varios espacios de datos SaaS después de configurar las claves de API de Adobe AI
description: Este artículo proporciona una solución a los problemas en los que solo ve un espacio de datos SaaS después de configurar las claves de API para Adobe AI.
exl-id: e13041da-b122-4684-8287-42132931f47a
feature: REST, Saas, Observability
role: Developer
source-git-commit: 61f5a526a0c36c91739103c0802bc9794a425f38
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# No se pueden ver varios espacios de datos SaaS después de configurar las claves de API de Adobe AI

Después de configurar las claves API para un servicio de Commerce como los servicios de Adobe AI (Product Recommendations o Live Search) o los servicios de pago para Adobe Commerce, verá varios espacios de datos de SaaS en el conector de servicios de Commerce. Según la asignación de derechos del producto y el tipo de implementación, el conector muestra solo un espacio de datos SaaS, que es el comportamiento esperado.

## Productos y versiones afectados

* Adobe Commerce (todos los métodos de implementación): todas las versiones
* Magento Open Source: todas las versiones
* Extensión o tecnología (Fastly, New Relic, etc.), Adobe AI (Product Recommendations/Live Search)

## Problema

Después de configurar las claves de la API de Adobe AI, el sistema solo muestra un espacio de datos SaaS.

## Causa

El número de espacios de datos de SaaS disponibles depende de la asignación de derechos de producto a la cuenta de Commerce y del tipo de servicio que se utilice.

## Solución

En general, el número de espacios de datos SaaS disponibles depende de la licencia de Commerce:

* Adobe Commerce: un espacio de datos de producción y dos de prueba
* Magento Open Source: un espacio de datos de producción y ningún espacio de datos de prueba

En Servicios de pago, el comportamiento predeterminado es:

* Los servicios de pago en Adobe Commerce (*Cloud o local*) tienen tres espacios de datos de manera predeterminada:
* un espacio de datos de producción
* dos espacios de datos de prueba
* Payment Services en Magento Open Source tiene un espacio de datos de forma predeterminada

Los clientes que sean propietarios de varios proyectos en la nube o instalaciones locales (*live/production*) también pueden solicitar espacios de datos de producción y prueba adicionales para cada proyecto o instancia enviando una solicitud de soporte técnico.

Los clientes de Magento Open Source que utilicen Adobe Payment Services también pueden solicitar un espacio de datos adicional. Póngase en contacto con el equipo de pagos para obtener una aprobación previa antes de enviar una solicitud de asistencia técnica para añadir un espacio de datos de prueba.

>[!NOTE]
> * No utilice el mismo espacio de datos SaaS en varios entornos al mismo tiempo. Si se reutiliza un espacio de datos de producción o prueba en entornos diferentes, los datos pueden mezclarse y pueden requerir limpieza.
> * Los servicios de pago de Adobe Commerce (*Cloud/On-Prem*) tienen tres espacios de datos de manera predeterminada.
> * Payment Services en Magento Open Source tiene un espacio de datos de forma predeterminada.
> Para solicitar espacios de datos adicionales:
> * Los clientes de Magento Open Source que utilicen Adobe Payment Services pueden solicitar un espacio de datos adicional. Póngase en contacto con el equipo de pagos para obtener la aprobación previa antes de enviar una solicitud de asistencia técnica con el fin de obtener un espacio de datos de prueba.
> * Los clientes que sean propietarios de varios proyectos en la nube o instalaciones locales (*live/production*) también pueden solicitar espacios de datos de producción y prueba adicionales para cada proyecto o instancia enviando una solicitud de soporte técnico.

## Lectura relacionada

[Aprovisionamiento de espacio de datos SaaS](https://experienceleague.adobe.com/en/docs/commerce/user-guides/integration-services/saas?lang=en#saas-data-space-provisioning)
