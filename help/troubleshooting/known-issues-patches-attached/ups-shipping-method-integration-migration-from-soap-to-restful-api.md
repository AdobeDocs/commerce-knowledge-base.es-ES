---
title: '[!DNL UPS] migración de integración de método de envío desde [!DNL SOAP] hasta [!DNL RESTful API]'
promoted: true
description: Aplique un parche para hacer frente a la [!DNL UPS] migración de integración de método de envío desde [!DNL SOAP] hasta [!DNL RESTful API] para Adobe Commerce 2.4.4 - 2.4.6-pX.
feature: Shipping/Delivery
role: Developer
exl-id: 8ab5d4a8-0155-4b2c-ab67-d0bd2f949a07
source-git-commit: 7785a37e033bc2bea5b6a1509c337289e7b871cb
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# [!DNL UPS] migración de integración de método de envío desde [!DNL SOAP] hasta [!DNL RESTful API]

>[!NOTE]
>
>Si ha cargado cualquiera de los tres parches de este artículo antes de que **10 de octubre de 2023**, debe volver a aplicar uno de estos parches ahora publicado en este artículo para su versión 2.4.4+/2.4.5+/2.4.6+ de Adobe Commerce/Magento Open Source una vez más, porque, de lo contrario, no podrá seleccionar y configurar parches específicos [!DNL UPS] métodos de envío en la **[!DNL Admin configuration]**, y tendrá que tener todos ellos habilitados. Estos nuevos parches son compatibles con los parches lanzados anteriormente.

Este artículo proporciona un parche para resolver problemas con [!DNL United Parcel Service (UPS)] migración de integración de método de envío desde [!DNL SOAP] hasta [!DNL RESTful API] para Adobe Commerce 2.4.4 - 2.4.6-pX.

Según las últimas actualizaciones de [!DNL UPS API] Modelo de seguridad, [!DNL UPS] ha implementado un [!DNL OAuth 2.0] modelo de seguridad para todos [!DNL APIs] (Más detalles disponibles en la [[!DNL UPS] Guía de migración de claves de acceso al portal para desarrolladores](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914)) para mejorar la seguridad general con el fin de reducir el fraude y proporcionar [!DNL API] funciones.

Este cambio afecta a nuestro [!DNL UPS] implementación de la integración de métodos de envío en Adobe Commerce y requiere que corrijamos nuestra implementación actual y migremos de [!DNL SOAP API] a la [!DNL RESTful API] para poder admitir [!DNL OAuth 2.0] protocolos de autenticación.

**A partir de junio de 2024**, los comerciantes de Adobe Commerce no podrán realizar transacciones con nuestro [!DNL UPS] integración, por lo que lanzamos esta revisión, que permite a los comerciantes de Adobe Commerce 2.4.4+/2.4.5+/2.4.6+ migrar a la última versión [!DNL UPS REST APIs].

Este problema se solucionará en la versión 2.4.7 de Adobe Commerce/Magento Open Source y también se incluirá en la versión 2.4.7-beta2 en octubre de 2023.

## Productos y versiones afectados

Adobe Commerce en infraestructura en la nube y local, y Magento Open Source:

* 2.4.4
* 2.4.4-pX
* 2.4.5
* 2,4,5-pX
* 2.4.6
* 2.4.6-pX

## Causa

El [!DNL UPS] liberado como [actualización de seguridad para su [!DNL API]](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914).

## Solución

Utilice los siguientes parches adjuntos, según la versión de Adobe Commerce/Magento Open Source:

Para resolver el problema en las versiones 2.4.4+, 2.4.5+ y 2.4.6+, debe aplicar el parche correspondiente a su versión de Adobe Commerce/Magento Open Source a continuación.

## Parche

Utilice los siguientes parches adjuntos, según la versión de Adobe Commerce/Magento Open Source:

### Para las versiones 2.4.4, 2.4.4-pX:

* [AC-9363_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip](assets/AC-9646_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip)

### Para las versiones 2.4.5, 2.4.5-pX:

* [AC-9358_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip](assets/AC-9647_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip)

### Para las versiones 2.4.6, 2.4.6-pX:

* [AC-9345_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip](assets/AC-9648_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip)

## Cómo aplicar el parche

Descomprima el archivo y consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) en nuestra base de conocimiento de asistencia para obtener instrucciones.

## Cómo saber si se han aplicado los parches

Teniendo en cuenta que no es posible comprobar fácilmente si el problema se ha corregido, es posible que desee comprobar si el parche se ha aplicado correctamente. Esto utiliza (ejemplo: *AC-9363*) como parche que se debe comprobar.

<u>Para ello, siga los siguientes pasos</u>:

1. [Instale el [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Ejecute el comando:

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. Debería ver una salida similar a esta, donde AC-9363 devuelve el *Aplicado* estado:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
