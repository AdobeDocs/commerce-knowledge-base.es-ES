---
title: 'MBI: volver a autenticar integraciones'
description: Este artículo proporciona soluciones para volver a autorizar una integración con el fin de otorgar a Magento Business Intelligence (MBI) los privilegios necesarios para extraer datos de un servicio de terceros. Se requiere la reautorización cuando se revocan estos privilegios.
exl-id: c608d6f9-64a5-44f8-9d7b-9a85a2668775
feature: Commerce Intelligence, Integration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 3cd14413-6539-5c64-b063-fdcabf03abff
    internal-label: Commerce Intelligence
  - id: cc04bd17-78d5-5120-8c3d-1b8a57e49280
    internal-label: Integration
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%
---
# MBI: volver a autenticar integraciones

Este artículo proporciona soluciones para volver a autorizar una integración con el fin de otorgar a Magento Business Intelligence (MBI) los privilegios necesarios para extraer datos de un servicio de terceros. Se requiere la reautorización cuando se revocan estos privilegios.

## Integraciones de bases de datos y SaaS

Para obtener listas de integraciones de bases de datos y SaaS, consulte [Conexión de datos externos mediante una integración](https://experienceleague.adobe.com/en/docs/commerce-business-intelligence/mbi/analyze/saas/integrations) en nuestra documentación para desarrolladores. (Al abrir la página, utilice la tabla de contenido de la izquierda para navegar).

## ¿Tiene problemas de conexión?

La autorización de una integración otorga a MBI los privilegios necesarios para extraer datos de un servicio de terceros. Se requiere la reautorización cuando se revocan estos privilegios.

Esto puede deberse a varias razones:

* Se ha corregido un problema con el servicio de terceros
* caducidad del token de autenticación
* un cambio realizado en su cuenta administrativa
* o un problema interno de MBI

El estado de todas las integraciones se encuentra en la página Integraciones ( **Administrar datos > Integraciones** ):

![Integraciones_page.png](assets/Integrations_page.png)

Para volver a autenticarse, es posible que tenga que volver a introducir las credenciales de la cuenta. En algunos casos, es posible que deba generar nuevas claves API para la integración problemática. Haga clic en el nombre de la integración del problema para iniciar el proceso de reautorización.

Si el problema persiste, [envíe un ticket de asistencia](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket).
