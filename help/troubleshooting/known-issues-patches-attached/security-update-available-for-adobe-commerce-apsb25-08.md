---
title: Actualización de seguridad disponible para Adobe Commerce - [!DNL APSB25-08]
promoted: true
description: Aplique un parche aislado para corregir  [!DNL critical, important, and moderate vulnerabilities] para Adobe Commerce 2.4.8-beta1, 2.4.7-p3, 2.4.6-p8, 2.4.5-p10, 2.4.4-p11 y versiones anteriores.
feature: Compliance, Security
role: Developer
exl-id: 567e6ad2-704e-461f-a54d-75f6bd96e996
source-git-commit: babb822cc505e2911ae28cd1a2540799146f19b3
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# Actualización de seguridad disponible para Adobe Commerce - [!DNL APSB25-08]

El 11 de febrero de 2025, Adobe lanzó una actualización de seguridad programada regularmente para Adobe Commerce y Magento Open Source. Esta actualización resuelve [[!DNL critical, important] y  [!DNL moderate]](https://helpx.adobe.com/security/severity-ratings.html) vulnerabilidades. La explotación exitosa de estas vulnerabilidades podría llevar a la ejecución de código arbitrario, la omisión de funciones de seguridad y la escalación de privilegios. Encontrará más información en el [Boletín de seguridad de Adobe ([!DNL APSB25-08]) aquí](https://helpx.adobe.com/security/products/magento/apsb25-08.html).

>[!NOTE]
>
>**Para ayudar a garantizar que la corrección de [!DNL CVE-2025-24434], indicada en el boletín de seguridad anterior, se pueda aplicar lo antes posible, Adobe también ha lanzado una revisión aislada que resuelve [!DNL CVE-2025-24434]. Esto permite a los comerciantes aplicar la corrección de forma aislada con menos riesgos de retraso debido a posibles problemas de integración.**

**Aplique las actualizaciones de seguridad más recientes lo antes posible. Si no lo hace, será vulnerable a estos problemas de seguridad y Adobe tendrá medios limitados para remediar el problema aún más.**

>[!NOTE]
>
>Póngase en contacto con los servicios de soporte si tiene algún problema al aplicar el parche de seguridad o el parche aislado.

## Productos y versiones afectados

Adobe Commerce en infraestructura en la nube, Adobe Commerce local y Magento Open Source:

* 2.4.8-beta1 y anteriores
* 2.4.7-p3 y anteriores
* 2.4.6-p8 y anteriores
* 2.4.5-p10 y anteriores
* 2.4.4-p11 y anteriores

## Solución para Adobe Commerce en la nube, Adobe Commerce local y software de Magento Open Source

Para ayudar a resolver la vulnerabilidad de los productos y las versiones afectados, debe aplicar el parche aislado [!DNL CVE-2025-24434], según la versión de Adobe Commerce/Magento Open Source.

## Detalles de parches aislados

Utilice los siguientes parches aislados adjuntos, según la versión de Adobe Commerce/Magento Open Source:

### Para la versión 2.4.8-beta1:

* [vuln-28982-2-4-8x-v2-composer-patch.zip](assets/vuln-28982-2-4-8x-v2-composer-patch.zip)

### Para las versiones 2.4.7, 2.4.7-p1, 2.4.7-p2, 2.4.7-p3:

* [vuln-28982-2-4-7x-v2-composer-patch.zip](assets/vuln-28982-2-4-7x-v2-composer-patch.zip)

### Para las versiones 2.4.6, 2.4.6-p1, 2.4.6-p2, 2.4.6-p3, 2.4.6-p4, 2.4.6-p5, 2.4.6-p6, 2.4.6-p7, 2.4.6-p8:

* [vuln-28982-2-4-6x-v2-composer-patch.zip](assets/vuln-28982-2-4-6x-v2-composer-patch.zip)

### Para las versiones 2.4.5, 2.4.5-p1, 2.4.5-p2, 2.4.5-p3, 2.4.5-p4, 2.4.5-p5, 2.4.5-p6, 2.4.5-p7, 2.4.5-p8, 2.4.5-p9, 2.4.5-p10:

* [vuln-28982-2-4-5x-v2-composer-patch.zip](assets/vuln-28982-2-4-5x-v2-composer-patch.zip)

### Para las versiones 2.4.4, 2.4.4-p1, 2.4.4-p2, 2.4.4-p3, 2.4.4-p4, 2.4.4-p5, 2.4.4-p6, 2.4.4-p7, 2.4.4-p8, 2.4.4-p9, 2.4.4-p10, 2.4.4-p11:

* [vuln-28982-2-4-4x-v2-composer-patch.zip](assets/vuln-28982-2-4-4x-v2-composer-patch.zip)


## Cómo aplicar el parche aislado

Descomprima el archivo y vea [Cómo aplicar un parche del compositor proporcionado por Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) en nuestra base de conocimiento de asistencia para obtener instrucciones.

## Solo para comerciantes de Adobe Commerce en la nube: cómo saber si se han aplicado los parches aislados

Teniendo en cuenta que no es posible comprobar fácilmente si se ha aplicado un parche al problema, es posible que desee comprobar si el parche aislado de [!DNL CVE-2025-24434] se ha aplicado correctamente.

>[!NOTE]
>
><u>Para ello, siga los siguientes pasos y use el archivo `VULN-27015-2.4.7_COMPOSER.patch` **como ejemplo**</u>:

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

* [Boletín de seguridad de Adobe ([!DNL APSB25-08])](https://helpx.adobe.com/security/products/magento/apsb25-08.html)
* [Las últimas actualizaciones de seguridad disponibles para Adobe Commerce)](https://helpx.adobe.com/security/products/magento.html)
