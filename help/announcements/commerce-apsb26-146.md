---
title: Acción urgente Actualización de seguridad crítica necesaria disponible para Adobe Commerce (APSB26-146)
description: Adobe ha lanzado el boletín de seguridad APSB26-146, que aborda CVE-2026-75650, una vulnerabilidad de día cero en Adobe Commerce. Obtenga información sobre cómo aplicar la revisión y rotar las credenciales.
autotag-review: '2026-09-07T17:27:44.037Z'
TQID: 'https://experienceleague.adobe.com/ADVRRn85--ZgWtPdi4qA49fsDPVW976N4MYWp26taho'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
  - id: c32adafa-ed01-4b31-997e-2413013911b0
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: e95fb4ca696be9f6d348ff66196565797575f74a
workflow-type: tm+mt
source-wordcount: 954
ht-degree: 0%

---


# Acción urgente necesaria: actualización de seguridad crítica disponible para Adobe Commerce (APSB26-146)

>[!IMPORTANT]
>
>Esta es una actualización urgente relacionada con CVE-2026-75650. Adobe es consciente de que el CVE-2026-75650 se ha explotado en la naturaleza para dirigirse a los comerciantes de Adobe Commerce.

El 7 de septiembre, Adobe lanzó una actualización de seguridad crítica que afecta a Adobe Commerce y Magento Open Source. Adobe tomó conciencia de una vulnerabilidad de día cero en Adobe Commerce y ha lanzado una actualización de seguridad (APSB26-146) para resolverla. La vulnerabilidad podría permitir que un atacante no autenticado ejecutara código arbitrario en una instalación afectada (CVE-2026-75650).

Adobe ha lanzado el boletín de seguridad APSB26-146, que aborda esta vulnerabilidad. El boletín está disponible aquí:

[Actualización de seguridad disponible para Adobe Commerce | APSB26-146](https://helpx.adobe.com/security/products/magento/apsb26-146.html)

En este artículo se explica cómo aplicar la revisión a las versiones actuales y anteriores de Adobe Commerce y Magento Open Source.

## Descripción

Productos y versiones afectados:

Versiones de Adobe Commerce:

* 2.4.9-2026-ago y anteriores
* 2.4.8-2026-ago y anteriores
* 2.4.7-2026-ago y anteriores
* 2.4.6-2026-ago y anteriores
* 2.4.5-2026-ago y anteriores
* 2.4.4-2026-ago y anteriores

Versiones B2B de Adobe Commerce:

* 1.5.3-2026-ago y anteriores
* 1.5.2-2026-ago y anteriores
* 1.4.2-2026-ago y anteriores
* 1.3.4-2026-ago y anteriores
* 1.3.3-2026-ago y anteriores

Versiones de Magento Open Source:

* 2.4.9-2026-ago y anteriores
* 2.4.8-2026-ago y anteriores
* 2.4.7-2026-ago y anteriores
* 2.4.6-2026-ago y anteriores

## Resolución

### Solución para Adobe Commerce en la nube, Adobe Commerce local y Magento Open Source

>[!NOTE]
>
>La revisión para CVE-2026-75650 ahora es compatible con todas las versiones de Adobe Commerce y Magento Open Source entre 2.4.4 y 2.4.7. Consulte la tabla siguiente y descargue el parche aplicable a su versión.

Para ayudar a resolver la vulnerabilidad de los productos y las versiones afectados, debe aplicar el **parche siguiente** (dependiendo de su versión) y girar las claves de cifrado.

| Número de versión | Parche |
|---|---|
| 2.4.9-2026-agosto, 2.4.8-2026-agosto, 2.4.7-2026-agosto, 2.4.6-2026-agosto, 2.4.5-2026-agosto, 2.4.4-2026-agosto, 2.4.9-2026-julio, 2.4.8-2026-julio, 2.4.7-2026-jul, 2.4.6-2026-jul, 2.4.5-2026-jul, 2.4.4-2026-jul, 2.4.8-p5, 2.4.8-p4, 2.4.8-p3, 2.4.7 -p10, 2.4.7 -p9, 2.4.6-p15, 2.4.6-p14, 2.4.5-p17, 2.4.5-p16, 2.4.4-p18, 2.4.4-p17 | [Revisión VULN-39341-composer-patch.zip](https://repo.magento.com/patch/VULN-39341-composer-patches.zip) |
| 2,4,8-p3, 2,4,8-p2 | [VULN-39341_248-p3.patch.zip](https://repo.magento.com/patch/VULN-39341-248-p3-patch.zip) |
| 2.4.8-p1, 2.4.8 | [VULN-39341_248-p1.patch.zip](https://repo.magento.com/patch/VULN-39341-248-p1-patch.zip) |
| 2.4.7-p8, 2.4.7-p7 | [VULN-39341_247-p8.patch.zip](https://repo.magento.com/patch/VULN-39341-247-p8-patch.zip) |
| 2.4.7: 2.4.7-p6 | [VULN-39341_247-p5.patch.zip](https://repo.magento.com/patch/VULN-39341-247-p5-patch.zip) |
| 2.4.6-p13, 2.4.6-p12, 2.4.5-p15, 2.4.5-p14, 2.4.4-p16, 2.4.4-p15 | [VULN-39341_246-p13.patch.zip](https://repo.magento.com/patch/VULN-39341-246-p13-patch.zip) |
| 2.4.6 - 2.4.6-p11, 2.4.5 - 2.4.5-p13, 2.4.4 - 2.4.4-p14 | [VULN-39341_246-p11.patch.zip](https://repo.magento.com/patch/VULN-39341-246-p11-patch.zip) |


{style="table-layout:auto"}

### Cómo aplicar la revisión

Descomprima el archivo y vea [Cómo aplicar un parche del compositor proporcionado por Adobe](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento) en nuestra base de conocimiento de asistencia para obtener instrucciones.

### Confirme que se ha aplicado la revisión (solo comerciantes de Adobe Commerce en la nube)

Teniendo en cuenta que no es posible determinar fácilmente si el problema se ha corregido, se recomienda comprobar si la revisión CVE-2026-75650 se ha aplicado correctamente.

Para ello, siga los siguientes pasos y use el archivo `VULN-39341_Hotfix_COMPOSER.patch` como ejemplo:

1. [Instalar la herramienta Parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage#install).
1. Ejecute el comando: `vendor/bin/magento-patches -n status | grep "39341\|Status"`.
1. Debería ver una salida similar a esta, donde este ejemplo VULN-39341 devuelve el estado Aplicado:

| ID | Título | Categoría | Origen | Estado | Detalle |
|---|---|---|---|---|---|
| N/D | .../m2-hotfixes/VULN-39341_Hotfix_COMPOSER.patch | Otros | Local | Aplicado | Tipo de parche: Personalizado |

### Rotar las credenciales después de aplicar el parche

Para solucionar este problema por completo, rote no solo la clave de cifrado, sino también todas las credenciales que se hayan cifrado o expuesto mediante ella, incluidas las credenciales del servidor, la API y la integración.

>[!NOTE]
>
>La clave de cifrado se utiliza para cifrar tokens de integración, credenciales de puerta de enlace de pago y tokens de automatización con privilegios del sistema. Rotar la clave de cifrado por sí sola no invalida las credenciales que ya se hayan expuesto. Rotar todas las credenciales asociadas en su origen (por ejemplo, en la pasarela de pago o el servicio de terceros), no solo dentro de Commerce.

Para rotar las credenciales, siga estos pasos:

1. Aplique la revisión.
1. Activar modo de mantenimiento.
1. Deshabilite la ejecución de cron (comando de Commerce en la nube: `vendor/bin/ece-tools cron:disable`).
1. [Rotar las claves de cifrado](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/encryption-key?lang=en).
1. Rotar todas las contraseñas de usuario del Panel de administración.
1. Desactive y vuelva a generar todos los tokens de integración de REST/SOAP/GraphQL (**[!UICONTROL System]** > **[!UICONTROL Extensions]** > **[!UICONTROL Integrations]**).
1. Rotar los secretos del cliente de OAuth para cualquier aplicación de terceros conectada.
1. Rotar las credenciales de la API de la puerta de enlace de pago al nivel del proveedor (Stripe, Braintree, Adyen, PayPal, etc.).
1. Rotar credenciales de base de datos.
1. Rotar las claves SSH/deploy y cualquier credencial de cuenta de servicio con privilegios del sistema o cron.
1. Rotar las claves API para el envío, los impuestos y otras extensiones de terceros integradas.
1. Vaciar la caché.
1. Habilitar la ejecución de cron (comando de Commerce en la nube: `vendor/bin/ece-tools cron:enable`).
1. Desactive el modo de mantenimiento.
1. Solo Commerce en la nube: vuelva a implementar para aplicar las nuevas credenciales de la base de datos.

### Actualizaciones de seguridad

Actualizaciones de seguridad disponibles para Adobe Commerce:

* [Boletín de seguridad de Adobe (APSB26-146)](https://helpx.adobe.com/security/products/magento/apsb26-146.html)
* [Las últimas actualizaciones de seguridad disponibles para Adobe Commerce](https://helpx.adobe.com/security/products/magento.html)

### Lectura relacionada

[Habilitar o deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode?lang=en) en la Guía de instalación de Adobe Commerce
