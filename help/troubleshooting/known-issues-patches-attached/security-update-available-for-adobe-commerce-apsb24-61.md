---
title: Actualización de seguridad disponible para Adobe Commerce - [!DNL APSB24-61]
promoted: true
description: Aplique un parche aislado para remediar  [!DNL CVE-2024-39397] solo para instancias de Adobe Commerce 2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10 y versiones anteriores que ejecuten [!DNL Apache].
feature: Compliance, Security
role: Developer
source-git-commit: 2038e766d65c81172391091a0cdff4abb04e84d5
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Actualización de seguridad disponible para Adobe Commerce - [!DNL APSB24-61]

El 13 de agosto de 2024, Adobe lanzó una actualización de seguridad para Adobe Commerce, Magento Open Source y el complemento Webhooks de Adobe Commerce.
Esta actualización resuelve [[!DNL critical, important] y  [!DNL moderate]](https://helpx.adobe.com/security/severity-ratings.html) vulnerabilidades. Una explotación exitosa podría llevar a la ejecución de código arbitrario, a la lectura arbitraria del sistema de archivos, a la omisión de características de seguridad y a la escalación de privilegios. El boletín es [Boletín de seguridad del Adobe ([!DNL APSB24-61])](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

>[!NOTE]
>
>**[!DNL CVE-2024-39397]solo es aplicable cuando se utiliza el servidor web [!DNL Apache].** Para garantizar que la corrección de esta vulnerabilidad se pueda aplicar lo antes posible, Adobe también ha lanzado un parche aislado que resuelve [!DNL CVE-2024-39397].

**Aplique las actualizaciones de seguridad más recientes lo antes posible. Si no lo hace, será vulnerable a estos problemas de seguridad y el Adobe tendrá medios limitados para ayudar a remediar.**

>[!NOTE]
>
>Póngase en contacto con los servicios de soporte si tiene algún problema al aplicar el parche de seguridad o el parche aislado.

## Productos y versiones afectados

Adobe Commerce en la nube, Adobe Commerce local y Magento Open Source:

* 2.4.7-p1 y anteriores
* 2.4.6-p6 y anteriores
* 2.4.5-p8 y anteriores
* 2.4.4-p9 y anteriores

## Solución para Adobe Commerce en la nube, software local de Adobe Commerce y Magento Open Source

Para ayudar a resolver la vulnerabilidad de los productos y las versiones afectados, debe aplicar el parche aislado [!DNL CVE-2024-39397].

## Detalles de parches aislados

Utilice el siguiente parche aislado adjunto:

* [acsd-60551-composer-patch.zip](assets/acsd-60551-composer-patch.zip)

## Cómo aplicar el parche aislado

Descomprima el archivo y vea [Cómo aplicar un parche del compositor proporcionado por el Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) en nuestra base de conocimiento de asistencia para obtener instrucciones.

## Solo para comerciantes de Adobe Commerce en la nube: cómo saber si se han aplicado los parches aislados

Teniendo en cuenta que no es posible comprobar fácilmente si se ha aplicado un parche al problema, es posible que desee comprobar si el parche aislado de [!DNL CVE-2024-39397] se ha aplicado correctamente.

<u>Para ello, siga los siguientes pasos y use el archivo `VULN-27015-2.4.7_COMPOSER.patch` como ejemplo</u>:

1. [Instalar la herramienta Parches de calidad](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Ejecute el comando:<br>
   ![cve-2024-34102-tell-if-patch-applied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. Debería ver una salida similar a esta, donde VULN-27015 devuelve el estado *Aplicado*:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->

## Actualizaciones de seguridad

Actualizaciones de seguridad disponibles para Adobe Commerce:

* [Boletín de seguridad de Adobe ([!DNL APSB24-61])](https://helpx.adobe.com/security/products/magento/apsb24-61.html)
