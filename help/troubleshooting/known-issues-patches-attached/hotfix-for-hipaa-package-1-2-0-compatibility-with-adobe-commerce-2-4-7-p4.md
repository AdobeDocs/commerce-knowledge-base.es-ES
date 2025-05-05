---
title: Revisión del paquete de compatibilidad con Adobe Commerce 2.4.7-p4 [!DNL HIPAA] 1.2.0
description: Este artículo proporciona una revisión para agregar compatibilidad para el nuevo  [!DNL HIPAA] paquete 1.2.0 con Adobe Commerce en la infraestructura en la nube 2.4.7-p4
feature: Install, Upgrade, Security, Compliance
role: Developer
source-git-commit: 705c43d2328d47fb5f00ae582a2a623ca9f94f70
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Revisión del paquete de compatibilidad con Adobe Commerce 2.4.7-p4 [!DNL HIPAA] 1.2.0

Este artículo proporciona una revisión para agregar compatibilidad para el nuevo paquete 1.2.0 **de**&#x200B;[!DNL HIPAA] con Adobe Commerce en la infraestructura en la nube 2.4.7-p4.

Este problema se solucionará en la versión 2.4.7-p5 de.

## Versiones y productos afectados

Adobe Commerce en infraestructura en la nube 2.4.7-p4 y anteriores

## Requisitos previos

* Adobe ha aprovisionado su cuenta de Adobe Commerce para tener acceso a la extensión **[!DNL HIPAA Ready]**. Consulte [[!DNL HIPAA] preparación en Adobe Commerce](https://experienceleague.adobe.com/es/docs/commerce-admin/start/compliance/hipaa-ready-service/overview) para obtener más información en **Adobe Commerce: Guía de introducción**.
* Acceda a [repo.magento.com](https://repo.magento.com) para instalar la extensión. Para obtener la generación de claves y los derechos necesarios, consulta [Obtener tus claves de autenticación](https://experienceleague.adobe.com/es/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) en nuestra **Guía de instalación de Adobe Commerce**.

## Problema

El paquete 1.1.0 de [!DNL HIPAA] no es compatible con la línea de versión de Adobe Commerce 2.4.7x.

## Solución

A través de esta revisión, los comerciantes que ejecuten Adobe Commerce en la infraestructura en la nube 2.4.7-p4 podrán usar el paquete 1.2.0 de [!DNL HIPAA].

>[!NOTE]
>
>**[!DNL HIPAA]1.2.0 solo es compatible con Adobe Commerce 2.4.7-p5. Si desea agregar compatibilidad con [!DNL HIPAA] 1.2.0 a Adobe Commerce 2.4.7-p4, instale la revisión proporcionada.<br><u>Si no está en Adobe Commerce 2.4.7-p4, primero debe actualizar a Adobe Commerce 2.4.7-p4 para poder usar este parche</u>.**

Para solucionar el problema de Adobe Commerce en la infraestructura en la nube 2.4.7-p4, debe aplicar el parche:

[ac-13382--patch-for-hipaa-2-4-7-p4-composer-patch.zip](assets/ac-13382--patch-for-hipaa-2-4-7-p4-composer-patch.zip)

## Cómo aplicar el parche

Descomprima el archivo y vea [Cómo aplicar un parche del compositor proporcionado por Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=es) en nuestra base de conocimiento de asistencia para obtener instrucciones.

## Solo para comerciantes de Adobe Commerce en la nube: cómo saber si se ha aplicado el parche

Teniendo en cuenta que no es posible comprobar fácilmente si el problema se ha corregido, es posible que desee comprobar si el parche se ha aplicado correctamente.

>[!NOTE]
>
><u>Puede hacerlo siguiendo estos pasos, usando el archivo `VULN-27015-2.4.7_COMPOSER.patch` **como ejemplo**</u>:

1. [Instalar la herramienta Parches de calidad](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es).
1. Ejecute el comando:<br>
   ![cve-2024-34102-tell-if-patch-applied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. Debería ver una salida similar a esta, **<u>donde el ejemplo usado aquí, VULN-27015</u>**, devuelve el estado *Aplicado*:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->
