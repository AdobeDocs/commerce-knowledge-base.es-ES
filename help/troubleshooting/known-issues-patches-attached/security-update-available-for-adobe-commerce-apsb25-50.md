---
title: Actualización de seguridad disponible para Adobe Commerce - [!DNL APSB25-50]
promoted: true
description: Aplique un parche aislado para corregir  [!DNL critical and important vulnerabilities] para Adobe Commerce 2.4.8, 2.4.7-p5, 2.4.6-p10, 2.4.5-p12, 2.4.4-p13 y versiones anteriores.
feature: Compliance, Security
role: Developer
source-git-commit: 9df7dee77bec7ffe4323f21e44d555338a0b1934
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# Actualización de seguridad disponible para Adobe Commerce - [!DNL APSB25-50]

El 10 de junio de 2025, Adobe lanzó una actualización de seguridad programada regularmente para Adobe Commerce y Magento Open Source. Esta actualización resuelve las vulnerabilidades [[!DNL critical] y [!DNL important]](https://helpx.adobe.com/es/security/severity-ratings.html). La explotación exitosa de estas vulnerabilidades podría conducir a la omisión de características de seguridad, escalación de privilegios y ejecución de código arbitrario.

Encontrará más información en el [Boletín de seguridad de Adobe ([!DNL APSB25-50]) aquí](https://helpx.adobe.com/security/products/magento/apsb25-50.html).

>[!NOTE]
>
>**Para ayudar a garantizar que la corrección de [!DNL CVE-2025-47110] enumerada en el boletín de seguridad anterior, se pueda aplicar lo antes posible, Adobe también ha lanzado una revisión aislada que resuelve [!DNL CVE-2025-47110]. Esto permite a los comerciantes aplicar la corrección de forma aislada con menos riesgos de retraso debido a posibles problemas de integración.**

**Aplique las actualizaciones de seguridad más recientes lo antes posible. Si no lo hace, será vulnerable a estos problemas de seguridad y Adobe tendrá medios limitados para remediar el problema aún más.**

Puede leer más sobre [nuestro proceso de implementación de parches aislados aquí.](https://business.adobe.com/blog/introducing-enhanced-security-patch-deployment-and-communications-in-adobe-commerce)

>[!NOTE]
>
>Para los clientes de Adobe Commerce en Managed Services, su ingeniero de éxito del cliente puede proporcionar directrices adicionales para aplicar el parche.

>[!NOTE]
>
>Póngase en contacto con los servicios de soporte si tiene algún problema al aplicar el parche de seguridad o el parche aislado.

Como recordatorio, aquí puede encontrar [las últimas actualizaciones de seguridad disponibles para Adobe Commerce.](https://helpx.adobe.com/es/security/products/magento.html)

## Productos y versiones afectados

Adobe Commerce (todos los métodos de implementación):

* 2.4.8
* 2.4.7-p5 y anteriores
* 2.4.6-p10 y anteriores
* 2.4.5-p12 y anteriores
* 2.4.4-p13 y anteriores

## Problemas

### I. CVE-2025-47110: XSS almacenado mediante inyección de plantillas del lado del servidor en Adobe Commerce 2.4.7-p4

<u>Productos y versiones afectados</u>:

Adobe Commerce (todos los métodos de implementación):

* 2.4.8
* 2.4.7-p5 y anteriores
* 2.4.6-p10 y anteriores
* 2.4.5-p12 y anteriores
* 2.4.4-p13 y anteriores

<u>Solución</u>:

Para las versiones de Adobe Commerce:

* 2.4.8
* 2.4.7, 2.4.7-p1, 2.4.7-p2, 2.4.7-p3, 2.4.7-p4, 2.4.7-p5
* 2.4.6, 2.4.6-p1, 2.4.6-p2, 2.4.6-p3, 2.4.6-p4, 2.4.6-p5, 2.4.6-p6, 2.4.6-p7, 2.4.6-p8, 2.4.6-p1
* 2.4.5, 2.4.5-p1, 2.4.5-p2, 2.4.5-p3, 2.4.5-p4, 2.4.5-p5, 2.4.5-p6, 2.4.5-p7, 2.4.5-p8, 2.4.5-p9, 2.4.5-p10, 2.4.5-p11, 2.4.5-p12
* 2.4.4, 2.4.4-p1, 2.4.4-p2, 2.4.4-p3, 2.4.4-p4, 2.4.4-p5, 2.4.4-p6, 2.4.4-p7, 2.4.4-p8, 2.4.4-p9, 2.4.4-p10, 2.4.4-p11, 2.4.4-p12, 2.4.4-p13

**Aplique la siguiente revisión aislada o actualice a la última revisión de seguridad.**

* **[VULN-31609_2.4.X.patch](assets/VULN-31609_2.4.X_patch.zip)**

### II. VULN-31547: XSS reflejado en marketplace.magento.com + un problema de ensamblaje para pedido de un solo clic que afecta a las instancias de IMS

<u>Productos y versiones afectados</u>:

Adobe Commerce (todos los métodos de implementación):

* 2.4.8

<u>Solución</u>:

Para las versiones de Adobe Commerce:

* 2.4.8

**Aplique la siguiente revisión aislada o actualice a la última revisión de seguridad.**

* **[VULN-31547_2.4.8.patch](assets/VULN-31547_2.4.8_patch.zip)**

## Cómo aplicar el parche aislado

Descomprima el archivo y vea [Cómo aplicar un parche del compositor proporcionado por Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=es) en nuestra base de conocimiento de asistencia para obtener instrucciones.

## Solo para comerciantes de Adobe Commerce en la nube: cómo saber si se han aplicado los parches aislados

Teniendo en cuenta que no es posible comprobar fácilmente si se ha aplicado un parche al problema, es posible que desee comprobar si el parche aislado de [!DNL CVE-2025-47110] se ha aplicado correctamente.

>[!NOTE]
>
><u>Puede hacerlo siguiendo estos pasos, usando el archivo `VULN-27015-2.4.7_COMPOSER.patch` **como EJEMPLO**</u>:

1. [Instalar la herramienta Parches de calidad](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es).
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

* [Boletín de seguridad de Adobe ([!DNL APSB25-50])](https://helpx.adobe.com/security/products/magento/apsb25-50.html)
* [Las últimas actualizaciones de seguridad disponibles para Adobe Commerce](https://helpx.adobe.com/es/security/products/magento.html)
