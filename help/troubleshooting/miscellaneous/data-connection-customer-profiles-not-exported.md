---
title: Los perfiles de cliente no aparecen en el Experience Platform
description: Este artículo proporciona pasos para la solución de problemas si los datos de perfil del cliente no aparecen en el Experience Platform al usar la extensión  [!DNL Data Connection] .
feature: Personalization, Integration, Configuration
role: Admin, Developer
exl-id: 4f12b032-0bee-47da-927a-8d4c2d8b8276
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# Los perfiles de cliente no aparecen en el Experience Platform

Este artículo proporciona pasos de solución de problemas si los datos de perfil del cliente no aparecen en el Experience Platform al utilizar la extensión de conexión de datos.

## Productos y versiones afectados

* Adobe Commerce 2.4.x con la extensión [!DNL Data Connection] instalada

## Problema

Ha instalado y configurado la extensión [[!DNL Data Connection]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview) y ha habilitado el envío de datos de perfil de cliente al Experience Platform, pero esos datos de perfil no aparecen en el Experience Platform.

## Solución

Si la información del perfil del cliente no aparece en el Experience Platform, compruebe lo siguiente:

### Confirme que está instalada la última versión de [!DNL Data Connection]

Asegúrese de que ha instalado la última versión de la extensión `experience-platform-connector`.

Consulte las [[!DNL Data Connection] notas de la versión de la extensión](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/release-notes) para obtener información sobre la versión más reciente.

>[!NOTE]
>
>La última versión de la extensión [!DNL Data Connection] incluye el módulo `customers-connector`, que es responsable de enviar datos de perfil al Experience Platform. El módulo `customers-connector` debe ser de la versión `1.2.0` o superior.

### Confirme que el módulo customer-connector está configurado.

Confirme que el módulo `customers-connector` está configurado según el escenario de instalación.

#### Infraestructura de Adobe Commerce en la nube

1. Habilitar la variable global `ENABLE_EVENTING` en `.magento.env.yaml`. [Más información](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global).

   ```bash
       stage:
           global:
               ENABLE_EVENTING: true
   ```

1. Transfiera y envíe los archivos actualizados al entorno de Cloud. Cuando finalice la implementación, habilite el envío de eventos con el siguiente comando:

   ```bash
       bin/magento config:set adobe_io_events/eventing/enabled 1
   ```

#### Instalación local de Adobe Commerce

Ejecute los siguientes comandos para habilitar la generación de código y los eventos de Adobe Commerce:

```bash
   bin/magento events:generate:module
   bin/magento module:enable Magento_AdobeCommerceEvents
   bin/magento setup:upgrade
   bin/magento setup:di:compile
   bin/magento config:set adobe_io_events/eventing/enabled 1
```

### Confirme que ha habilitado la captura y el envío de datos de perfil al Experience Platform.

En el Administrador de Commerce, asegúrese de que están configurados los siguientes campos:

* En **[!UICONTROL System]** > **[!UICONTROL Services]** > **[!UICONTROL Data Connection]**, compruebe que las casillas de verificación [!UICONTROL Back office events] y [!UICONTROL Customer profiles] estén habilitadas.
* Asegúrese de que el campo *[!UICONTROL Profile Dataset ID]* es correcto y es un conjunto de datos diferente al que está utilizando actualmente para los datos de evento de comportamiento y de back-office.

### Comprobar si los eventos se enrutan a ensayo o producción

1. Ejecute el siguiente comando para mostrar el entorno actual de Adobe Developer:

   ```bash
   Copy code
   bin/magento config:show
   adobe_io_events/integration/adobe_io_environment
   ```

1. Si el entorno está establecido en *[!UICONTROL Stage]*, cámbielo a *[!UICONTROL Production]* con el siguiente comando:

   ```bash
   Copy code
   bin/magento config:set adobe_io_events/integration/adobe_io_environment
   production
   ```

### Tabla SaaS de datos de evento de consulta

Conecte y ejecute la siguiente consulta [!DNL SQL] para comprobar que los registros de perfil del cliente aparecen en la
`event_data_saas` y que no hay errores:

```sql
Copy code
select * from event_data_saas;
```

### Gestión de errores de publicación de eventos

1. Si encuentra el siguiente error, asegúrese de que las claves del conector SaaS de zona protegida y producción sean correctas:

   ```css
   Copy code
   2024-06-07 14:37:57 | 2024-06-07 14:38:03 | 1 | 0 | Event publishing
   failed: Error code: 403; reason: Forbidden { "error": { "code":
   "Forbidden", "message": "Client ID is invalid", "details": {
   "error_code": "403003" } } }
   ```

1. Vaya a la página *[!UICONTROL Commerce Services Connector]* en el Administrador y asegúrese de que las claves [!UICONTROL sandbox/production] especificadas estén correctamente configuradas. Confirme también que la configuración de la cuenta de Commerce [!UICONTROL sandbox/production] coincide con la que se muestra en [!UICONTROL Commerce Services Connector]. Más información [más](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas#apikey).

### Compruebe si el ID de servicio está en la lista de permitidos y confirme con el soporte de Adobe Commerce

1. Compruebe que [!UICONTROL Commerce Services Connector] `serviceId` aparece en la lista de permitidos en Adobe Commerce.
1. Póngase en contacto con el [soporte técnico de Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) para confirmar el estado de la lista de permitidos.

## Lectura relacionada

* Extensión [[!DNL Data Connection]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview) en la guía del usuario de Commerce Services
* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce
