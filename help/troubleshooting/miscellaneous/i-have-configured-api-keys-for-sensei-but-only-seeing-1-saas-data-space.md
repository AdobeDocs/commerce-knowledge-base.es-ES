---
title: He configurado las claves API para Sensei, pero solo veo un espacio de datos SaaS
description: Este artículo proporciona una solución a los problemas en los que solo ve un espacio de datos SaaS después de configurar las claves de API para Sensei.
exl-id: e13041da-b122-4684-8287-42132931f47a
feature: REST, Saas, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# He configurado las claves API para Sensei, pero solo veo un espacio de datos SaaS

Este artículo proporciona una solución a los problemas en los que solo ve un espacio de datos SaaS después de configurar las claves de API para Sensei.

## Productos y versiones afectados

* Adobe Commerce (todos los métodos de implementación): todas las versiones
* Magento Open Source: todas las versiones
* Extensión o tecnología (Fastly, New Relic, etc.), Adobe Sensei (Product Recommendations/Live Search)

## Problema

He configurado las claves API para Sensei, pero solo veo un espacio de datos SaaS.

## Causa

El número de espacios de datos SaaS que aparecen depende de la licencia de Commerce:

* Adobe Commerce: un espacio de datos de producción, dos espacios de datos de prueba
* Magento Open Source: un espacio de datos de producción, sin espacios de datos de prueba

## Solución

* Asegúrese de que las claves API se hayan creado en la cuenta del propietario de la cuenta. Incluso si se le ha concedido acceso compartido a su cuenta y se han creado las claves en su propia cuenta, esto no le otorgará más de un espacio de datos.
* Si las claves se generaron en la cuenta del propietario de la cuenta, asegúrese de que la licencia esté activa, es decir, que no haya facturas pendientes.
