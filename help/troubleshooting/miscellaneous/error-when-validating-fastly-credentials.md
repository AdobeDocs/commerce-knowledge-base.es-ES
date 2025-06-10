---
title: Error al validar las  [!DNL Fastly] credenciales
description: Este artículo proporciona una solución para el problema en el que un usuario obtiene un error al validar las  [!DNL Fastly] credenciales.
exl-id: 02104731-6666-47a6-abc6-215812f09915
feature: Configuration
role: Developer
source-git-commit: 838f0c5d55c29d026dc37a8f7e5214b9880a4353
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Error al validar las credenciales de [!DNL Fastly]

Este artículo explica cómo resolver los errores *Token caducado* que se encontraron al validar las credenciales de [!DNL Fastly].

Los pasos descritos en este artículo también se aplican si necesita rotar (ciclar) su token de API [!DNL Fastly] por motivos de seguridad. En estos casos, debe enviar un ticket de asistencia de Adobe Commerce para solicitar un nuevo token de API [!DNL Fastly].

## Problema

* Se produce un error al validar las credenciales de [!DNL Fastly].
* Sospecha que el token [!DNL Fastly] podría haberse visto comprometido, por ejemplo, si se compartió de forma involuntaria en un ticket de asistencia o se publicó en un foro público.

## Productos y versiones afectados

* Adobe Commerce (todos los métodos de implementación): Todas las versiones
* Extensión o tecnología ([!DNL Fastly], [!DNL New Relic], etc.) versión [!DNL Fastly]

## Solución

1. Asegúrese de que tiene el ID de servicio [!DNL Fastly] y el token de API correctos e intente validarlos de nuevo. Para obtener instrucciones detalladas, consulte [Probar las [!DNL Fastly] credenciales](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration?lang=en#test-the-fastly-credentials) en nuestra documentación para desarrolladores.
1. Si la verificación de las credenciales falla, ejecute el siguiente comando curl para confirmar el estado del servicio:

   ```curl
   curl -H "Fastly-Key: <API key>" https://api.fastly.com/service/<service ID>/version/active
   ```

1. Si el comando anterior devuelve un error similar a: `{"msg":"Token $TOKEN expired at 2021-09-28T02:03:37Z"}`, envíe un vale de soporte técnico para solicitar un nuevo token de API. Después de recibir el nuevo token, actualice la configuración en su entorno.

   Para obtener información sobre cómo enviar un vale de soporte, consulte [Guía del usuario del Centro de ayuda de Adobe Commerce > TICKETS DE SOPORTE](/help/help-center-guide/help-center/magento-help-center-user-guide.md#support-tickets) en nuestra base de conocimiento de soporte técnico.

   >[!NOTE]
   >
   >Nunca comparta contraseñas o tokens de API válidos/activos directamente en el ticket, ya que tendremos que revocar el token actual y generar uno nuevo por motivos de seguridad.
   >
   >El Soporte de Adobe Commerce tiene acceso a los tokens, por lo que no debe incluir esta información en el ticket.

1. Si el comando no devuelve el error, asegúrese de que está ejecutando la versión más reciente de la extensión [!DNL Fastly]. Si su versión es anterior a la de 1.2.203, primero debe hacer clic en **[!UICONTROL Save Config]** para poder probar las credenciales.

## Lecturas relacionadas en nuestra documentación para desarrolladores:

* [Nube para Adobe Commerce > [!DNL Fastly] > [!DNL Fastly] cuenta de servicio y credenciales](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly?lang=en#fastly-service-account-and-credentials)

* [Cloud for Adobe Commerce > Configurar [!DNL Fastly] > Probar las [!DNL Fastly] credenciales](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration?lang=en#test-the-fastly-credentials)
