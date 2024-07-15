---
title: '[!DNL USPS] revisión de soporte del método de envío Ground Advantage para AC-9182'
promoted: true
description: Aplique un parche para resolver el problema del método de envío  [!DNL USPS] Ground Advantage AC-9182 para Adobe Commerce 2.4.4 - 2.4.6-p2.
feature: Shipping/Delivery
role: Developer
exl-id: b6871d19-3d02-4026-82e6-3545f4ab7159
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# [!DNL USPS] revisión de soporte del método de envío Ground Advantage para AC-9182

Este artículo proporciona un parche para resolver el problema AC-9182 del nuevo método de envío **[!DNL USPS]Ground Advantage** en Adobe Commerce 2.4.4 - 2.4.6-p2.

El 9 de julio de 2023, el Servicio postal de los Estados Unidos ([!DNL USPS]) publicó un nuevo método de envío, [[!DNL USPS] Ground Advantage](https://www.usps.com/ship/ground-advantage.htm).

Este nuevo método de envío está reemplazando sus tres métodos de envío actuales principales:

* [!DNL USPS] terreno comercial
* [!DNL USPS] servicio de paquetes de primera clase
* [!DNL USPS] paquetería Seleccionar terreno

[[!DNL USPS] anunció](https://faq.usps.com/s/article/USPS-Ground-Advantage#how_it_works) que a partir del 30 de septiembre de 2023, estos tres métodos de envío se suspenderán y todos los clientes deberán usar el nuevo método **[!DNL USPS]Ground Advantage** en su lugar.

Por lo tanto, después del 30 de septiembre de 2023, todos los comerciantes de Adobe Commerce que usen el método de envío USPS ya no podrán obtener las tarifas de envío de [!DNL USPS] mediante estos tres métodos de envío heredados.

Este problema se solucionará en el ámbito de las próximas versiones de parches solo de seguridad de octubre de 2023, en las versiones 2.4.6-p3, 2.4.5-p5 y 2.4.4-p6.

## Productos y versiones afectados

Adobe Commerce en infraestructura en la nube y local, y Magento Open Source:

* 2.4.4
* 2.4.4-p1
* 2.4.4-p2
* 2.4.4-p3
* 2.4.4-p4
* 2.4.4-p5
* 2.4.5
* 2,4,5-p1
* 2,4,5-p2
* 2,4,5-p3
* 2.4.5-p4
* 2.4.6
* 2.4.6-p1
* 2.4.6-p2

## Causa

[!DNL USPS] realizó una actualización de [!DNL API].

## Solución

Para resolver el problema en las versiones 2.4.4, 2.4.5 y 2.4.6, debe aplicar el parche AC-9182 que aparece a continuación.

## Parche

El parche se adjunta a este artículo. Para descargarlo, haga clic en el siguiente vínculo:

[AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.zip](assets/AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.zip)

## Cómo aplicar el parche

Descomprima el archivo y vea [Cómo aplicar un parche del compositor proporcionado por el Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) en nuestra base de conocimiento de asistencia para obtener instrucciones.

## Cómo saber si se han aplicado los parches

Teniendo en cuenta que no es posible comprobar fácilmente si el problema se ha corregido, es posible que desee comprobar si el parche AC-9182 se ha aplicado correctamente.

<u>Para ello, siga los siguientes pasos</u>:

1. [Instalar [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Ejecute el comando:

   ```bash
   vendor/bin/magento-patches -n status |grep "9182|Status"
   ```

1. Debería ver una salida similar a esta, donde AC-9182 devuelve el estado *Aplicado*:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
