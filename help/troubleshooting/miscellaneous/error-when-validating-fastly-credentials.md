---
title: Error al validar las credenciales de Fastly
description: Este artículo proporciona una solución al problema en el que un usuario obtiene un error al validar las credenciales de Fastly.
exl-id: 02104731-6666-47a6-abc6-215812f09915
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Error al validar las credenciales de Fastly

Este artículo proporciona una solución al problema en el que un usuario obtiene un error al validar las credenciales de Fastly.

## Problema

El usuario recibe un error al validar las credenciales de Fastly.

## Productos y versiones afectados

* Adobe Commerce (todos los métodos de implementación): Todas las versiones
* Extensión o tecnología (Fastly, New Relic, etc.) versión Fastly

## Solución

1. Asegúrese de que tiene el ID de servicio de Fastly y el token de API correctos e intente validar de nuevo. Para obtener instrucciones detalladas, consulte [Probar las credenciales de Fastly](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#test-the-fastly-credentials) en nuestra documentación para desarrolladores.
1. Si la verificación de las credenciales falla, ejecute el siguiente comando curl para confirmar el estado del servicio:

   ```curl
   curl -H "Fastly-Key: <API key>" https://api.fastly.com/service/<service ID>/version/active
   ```

1. Si el comando anterior devuelve un error similar al siguiente: *{&quot;msg&quot;:&quot;Token $TOKEN caducó el 2021-09-28T02:03:37Z&quot;}*, envíe un vale de asistencia para solicitar un nuevo token de API.

   Para obtener información sobre cómo enviar un vale de soporte, consulte [Guía del usuario del Centro de ayuda de Adobe Commerce > TICKETS DE SOPORTE](/help/help-center-guide/help-center/magento-help-center-user-guide.md#support-tickets) en nuestra base de conocimiento de soporte técnico.

   >[!NOTE]
   >
   >Nunca comparta contraseñas o tokens de API válidos/activos directamente en el ticket, ya que tendremos que revocar el token actual y generar uno nuevo por motivos de seguridad.

1. Si el comando no devuelve el error, asegúrese de que está ejecutando la versión más reciente de la extensión [!DNL Fastly]. Si su versión es anterior a la de 1.2.203, primero debe hacer clic en **[!UICONTROL Save Config]** para poder probar las credenciales.

## Lecturas relacionadas en nuestra documentación para desarrolladores:

* [Cloud for Adobe Commerce > Fastly > Cuenta de servicio y credenciales de Fastly](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/cdn/fastly#fastly-service-account-and-credentials)

* [Cloud for Adobe Commerce > Configurar rápidamente > Probar las credenciales de Fastly](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#test-the-fastly-credentials)
