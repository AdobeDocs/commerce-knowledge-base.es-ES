---
title: Error "El código de área no está establecido" al ejecutar el programa de instalación:actualización
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce en la infraestructura en la nube 2.2.3 relacionado con el error *El código de área no está configurado* al ejecutar el comando setup:upgrade.
exl-id: ace92331-6022-49fa-a776-d06d841b3b32
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%
---
# Error &quot;El código de área no está establecido&quot; al ejecutar `setup:upgrade`

Este artículo proporciona un parche para el problema conocido de Adobe Commerce en la infraestructura en la nube 2.2.3 relacionado con la obtención del error *&quot;El código de área no está establecido&quot;* al ejecutar el siguiente comando:

```bash
setup:upgrade
```

>[!NOTE]
>
>El problema se solucionó en Adobe Commerce 2.2.4.

## Problema

Al ejecutar el

```bash
bin/magento setup:upgrade
```

del comando, recibe el siguiente mensaje de error: *&quot;Module &#39;Magento\_AdvancedSalesRule&#39;: Installing data...Area code not set: El código de área debe establecerse antes de iniciar una sesión&quot;* y se interrumpe la ejecución del comando. El problema aparece porque se solicita la configuración de área antes de que se establezca. El parche permite detectar el error y no interrumpir el proceso de actualización.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[Descargar MDVA-10439\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-10439_EE_2.2.3_COMPOSER_v1.patch.zip)

## Versiones de Adobe Commerce compatibles:

El parche se ha creado para:

* Adobe Commerce en la infraestructura en la nube 2.2.3

El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.2.0 - 2.2.3

## Cómo aplicar el parche

Para obtener instrucciones, consulte [Cómo aplicar un parche del compositor proporcionado por Adobe](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento) en nuestra base de conocimiento de soporte.

## Archivos adjuntos
