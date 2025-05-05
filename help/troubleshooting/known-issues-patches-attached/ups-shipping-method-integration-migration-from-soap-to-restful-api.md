---
title: '[!DNL UPS]: migración de la integración del método de envío de  [!DNL SOAP] a [!DNL RESTful API]'
promoted: true
description: Aplique un parche para hacer frente a la migración de la integración del método de envío  [!DNL UPS] de [!DNL SOAP] a [!DNL RESTful API] para Adobe Commerce 2.4.4 - 2.4.6-pX.
feature: Shipping/Delivery
role: Developer
exl-id: 8ab5d4a8-0155-4b2c-ab67-d0bd2f949a07
source-git-commit: 6694bb1e041e6285f5bd5a05a1c37b7062521f52
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# [!DNL UPS] migración de integración de método de envío de [!DNL SOAP] a [!DNL RESTful API]

>[!NOTE]
>
>Si cargó cualquiera de los tres parches de este artículo antes del **6 de junio de 2024**: Si tiene este problema debido a que no se están utilizando las mediciones de [!DNL Metric System/SI] (kilogramos y centímetros), debe volver a aplicar uno de estos parches nuevos y actualizados que ahora se publican en este artículo para su versión de Adobe Commerce/Magento Open Source 2.4.4+/2.4.5+/2.4.6+ una vez más, ya que, de lo contrario, no podrá seleccionar las mediciones de [!DNL Metric System/SI] kilogramos de **5&rbrace; y** centímetros **&rbrace; métodos de envío en &#x200B;** [!DNL Admin configuration]&#x200B;**.**&#x200B;[!DNL UPS] Estos nuevos parches son compatibles con los parches lanzados anteriormente. Este problema se solucionará de forma permanente en el ámbito de la próxima versión 2.4.7-p1 de Adobe Commerce, programada para el **11 de junio de 2024**.

>[!NOTE]
>
>Si has cargado cualquiera de los tres parches de este artículo antes del **10 de octubre de 2023**, deberías volver a aplicar uno de estos parches ahora publicados en este artículo para tu versión 2.4.4+/2.4.5+/2.4.6+ de Adobe Commerce/Magento Open Source una vez más, porque de lo contrario no podrás seleccionar y configurar [!DNL UPS] métodos de envío específicos en **[!DNL Admin configuration]**, y tendrás que tenerlos todos activados. Estos nuevos parches son compatibles con los parches lanzados anteriormente.

Este artículo proporciona un parche para resolver los problemas con la migración de la integración del método de envío [!DNL United Parcel Service (UPS)] de [!DNL SOAP] a [!DNL RESTful API] para Adobe Commerce 2.4.4 - 2.4.6-pX.

Según las últimas actualizaciones del modelo de seguridad de [!DNL UPS API], [!DNL UPS] ha implementado un modelo de seguridad de [!DNL OAuth 2.0] para todos los [!DNL APIs] (más detalles disponibles en la [[!DNL UPS] Guía de migración de claves de acceso al portal para desarrolladores](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914)) con el fin de mejorar la seguridad general para reducir el fraude y proporcionar capacidades mejoradas de [!DNL API].

Este cambio afecta nuestra implementación actual de la integración del método de envío [!DNL UPS] en Adobe Commerce y requiere que corrijamos nuestra implementación actual y que migremos de [!DNL SOAP API] a [!DNL RESTful API] para poder admitir los protocolos de autenticación [!DNL OAuth 2.0].

**A partir de junio de 2024**, los comerciantes de Adobe Commerce no podrán realizar transacciones con nuestra integración actual de [!DNL UPS], por lo que lanzamos esta revisión, que permite a los comerciantes de Adobe Commerce 2.4.4+/2.4.5+/2.4.6+ migrar a la versión más reciente de [!DNL UPS REST APIs].

Este problema se solucionará en la versión 2.4.7 de Adobe Commerce/Magento Open Source y también se incluirá en la versión 2.4.7-beta2 en octubre de 2023.

## Productos y versiones afectados

Adobe Commerce en infraestructura en la nube y local, y Magento Open Source:

* 2.4.4
* 2.4.4-pX
* 2.4.5
* 2,4,5-pX
* 2.4.6
* 2.4.6-pX

## Causas

[!DNL UPS] publicó una [actualización de seguridad para su [!DNL API]](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914).

Si tiene la Unión Europea (otros orígenes pueden experimentar el mismo problema) que el Origen del envío, se producirá un error en la solicitud [!DNL UPS REST]:
&quot;*Un envío no puede tener KGS/IN o LBS/CM u OZS/CM como unidad de medida.*&quot;

## Solución

Utilice los siguientes parches adjuntos, según la versión de Adobe Commerce/Magento Open Source:

Para resolver el problema en las versiones 2.4.4+, 2.4.5+ y 2.4.6+, debe aplicar el parche correspondiente a su versión de Adobe Commerce/Magento Open Source a continuación.

## Parche

Utilice los siguientes parches adjuntos, según la versión de Adobe Commerce/Magento Open Source:

### Para las versiones 2.4.4, 2.4.4-pX:

* [AC-11984_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip](assets/AC-11984_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip)

### Para las versiones 2.4.5, 2.4.5-pX:

* [AC-11983_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip](assets/AC-11983_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip)

### Para las versiones 2.4.6, 2.4.6-pX:

* [AC-11916_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip](assets/AC-11916_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip)

## Cómo aplicar el parche

Descomprima el archivo y vea [Cómo aplicar un parche del compositor proporcionado por el Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) en nuestra base de conocimiento de asistencia para obtener instrucciones.

## Cómo saber si se han aplicado los parches

Teniendo en cuenta que no es posible comprobar fácilmente si el problema se ha corregido, es posible que desee comprobar si el parche se ha aplicado correctamente. Esto usa (Ejemplo: *AC-9363*) como parche que se debe comprobar.

<u>Para ello, siga los siguientes pasos</u>:

1. [Instalar [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Ejecute el comando:

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. Debería ver una salida similar a esta, donde AC-9363 devuelve el estado *Aplicado*:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
