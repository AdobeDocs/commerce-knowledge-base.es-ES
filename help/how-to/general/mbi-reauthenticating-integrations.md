---
title: 'MBI: volver a autenticar integraciones'
description: Este artículo proporciona soluciones para volver a autorizar una integración con el fin de otorgar a Magento Business Intelligence (MBI) los privilegios necesarios para extraer datos de un servicio de terceros. Se requiere la reautorización cuando se revocan estos privilegios.
exl-id: c608d6f9-64a5-44f8-9d7b-9a85a2668775
feature: Commerce Intelligence, Integration
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# MBI: volver a autenticar integraciones

Este artículo proporciona soluciones para volver a autorizar una integración con el fin de otorgar a Magento Business Intelligence (MBI) los privilegios necesarios para extraer datos de un servicio de terceros. Se requiere la reautorización cuando se revocan estos privilegios.

## Integraciones de bases de datos y SaaS

Para obtener listas de integraciones de bases de datos y SaaS, consulte [Conexión de datos externos mediante una integración](https://experienceleague.adobe.com/es/docs/commerce-business-intelligence/mbi/analyze/saas/integrations) en nuestra documentación para desarrolladores. (Al abrir la página, utilice la tabla de contenido de la izquierda para navegar).

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

Si el problema persiste, [envíe un ticket de asistencia](https://experienceleague.adobe.com/es/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket).
