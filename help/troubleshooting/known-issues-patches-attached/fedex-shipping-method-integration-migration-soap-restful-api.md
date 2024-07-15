---
title: 'SOAP ''[!DNL FedEx]: migración de la integración del método de envío de la API de RESTful a la API de'''
promoted: true
description: SOAP Aplique un parche para lidiar con la migración de la integración del método de envío  [!DNL FedEx] de la API de RESTful a la API de Adobe Commerce 2.4.4-p4 - 2.4.6-pX.
feature: Shipping/Delivery
role: Developer
exl-id: 7e11a171-6924-41d0-a5c7-7b794d0da84c
source-git-commit: 7c468583883789a6bc6e41d1a787a356ea3205c4
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# SOAP [!DNL FedEx]: migración de la integración del método de envío de la API de a RESTful

SOAP Este artículo proporciona un parche para resolver los problemas con la migración de la integración del método de envío [!DNL FedEx] de la API de RESTful a la API de Adobe Commerce 2.4.4-p4 - 2.4.6-pX.

El seguimiento de [!DNL FedEx Web Services], la validación de direcciones y la validación de códigos postales de lenguajes de definición de servicios web (WSDLS) se retirarán el 15 de mayo de 2024. SOAP La base de datos [!DNL FedEx Web Services] se encuentra en la contención de desarrollo y se ha reemplazado con [!DNL FedEx] API RESTFUL. Para obtener más información, consulte [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

Este cambio afecta a nuestra implementación actual de la integración de métodos de envío [!DNL FedEx] en Adobe Commerce SOAP y requiere que corrijamos nuestra implementación actual y migremos de las API de obsoletas a las últimas [!DNL FedEx] API de RESTFUL.

A partir del 15 de mayo de 2024, los clientes de Adobe Commerce no podrán utilizar nuestra integración actual de método de envío [!DNL FedEx], por lo que Adobe lanzará esta revisión que permite a los clientes de Adobe Commerce SOAP 2.4.4+ utilizar las últimas API de RESTFUL [!DNL FedEx] en lugar de las obsoletas.


## Productos y versiones afectados

Adobe Commerce en infraestructura en la nube y local, y Magento Open Source:

* 2.4.4-p4
* 2.4.5
* 2,4,5-pX
* 2.4.6
* 2.4.6-pX

## Causa

SOAP [!DNL FedEx] ha desaprobado sus API basadas en el código de tiempo de ejecución de la y las ha reemplazado por las API RESTful. Consulte [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

## Solución

Utilice los siguientes parches adjuntos, según la versión de Adobe Commerce/Magento Open Source:

Para resolver el problema en las versiones 2.4.4+, 2.4.5+ y 2.4.6+, debe aplicar el parche correspondiente a su versión de Adobe Commerce/Magento Open Source a continuación.

## Parche

Utilice los siguientes parches adjuntos, según la versión de Adobe Commerce/Magento Open Source:

### Para las versiones 2.4.4-p4:

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)

### Para las versiones 2.4.5, 2.4.5-pX:

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)


### Para las versiones 2.4.6, 2.4.6-pX:


* [FedexPatch-Composer-246p3develop.patch.zip](assets/FedexPatch-Composer-246p3develop.patch.zip)


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
