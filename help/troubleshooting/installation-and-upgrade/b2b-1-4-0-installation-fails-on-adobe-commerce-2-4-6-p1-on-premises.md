---
title: La instalación de '[!DNL B2B] 1.4.0 falla en Adobe Commerce 2.4.6-p1 local'
description: Este artículo proporciona una solución para el problema local de Adobe Commerce 2.4.6-p1 en el que falla la instalación de la  [!DNL B2B] versión 1.4.0.
feature: Install, Upgrade, B2B
role: Developer
exl-id: 4a557c13-7ec2-4cfe-b86e-bb0d1a441658
source-git-commit: 35d4f2130d0ec71f71f5f20aa8a7c76207e7a35a
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# La instalación de [!DNL B2B] 1.4.0 falla en Adobe Commerce 2.4.6-p1 local

Este artículo proporciona una solución para el problema local de Adobe Commerce 2.4.6-p1 donde falla la instalación de [!DNL B2B] versión 1.4.0.

## Productos y versiones afectados

* Adobe Commerce 2.4.6-p1 **local**
* [!DNL B2B] versión 1.4.0

>[!NOTE]
>
>[!DNL B2B] versión 1.4.0 se instala correctamente en **Adobe Commerce Cloud 2.4.6-p1**.

## Problema

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce 2.4.6-p1.

   ```bash
   m2install.sh -s composer --ee -v 2.4.6-p1
   ```

1. Intente instalar [!DNL B2B] versión 1.4.0.

   ```bash
   composer require magento/extension-b2b:1.4.0
   ```

<u>Resultados esperados</u>:

[!DNL B2B] versión 1.4.0 se instala correctamente en Adobe Commerce 2.4.6-p1.

<u>Resultados reales</u>:

La instalación falla con el siguiente error:

```bash
Your requirements could not be resolved to an installable set of packages.

  Problem 1
    - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
    - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.


Installation failed, reverting ./composer.json and ./composer.lock to their original content.
```

## Solución

Instale o actualice correctamente [!DNL B2B] versión 1.4.0 en Adobe Commerce 2.4.6-p1 al agregar dependencias manuales para el paquete de seguridad [!DNL B2B] con una [etiqueta de estabilidad](https://getcomposer.org/doc/04-schema.md#package-links).

1. Desde el directorio de instalación de Adobe Commerce, actualice `composer.json` con las dependencias requeridas:

   ```bash
   composer require magento/module-re-captcha-company=1.0.3-beta1@beta magento/security-package-b2b=1.0.4-beta1@beta
   ```

   **Salida de comando:**

   ```bash
   Running composer update magento/module-re-captcha-company magento/security-package-b2b
   Loading composer repositories with package information
   Updating dependencies
   Lock file operations: 2 installs, 0 updates, 0 removals
     - Locking magento/module-re-captcha-company (1.0.3-beta1)
     - Locking magento/security-package-b2b (1.0.4-beta1)
   Writing lock file
   Installing dependencies from lock file (including require-dev)
   Package operations: 2 installs, 0 updates, 0 removals
     - Downloading magento/module-re-captcha-company (1.0.3-beta1)
     - Installing magento/module-re-captcha-company (1.0.3-beta1): Extracting archive
     - Installing magento/security-package-b2b (1.0.4-beta1)
   1 package suggestions were added by new dependencies, use `composer suggest` to see details.
   Package sebastian/phpcpd is abandoned, you should avoid using it. No replacement was suggested.
   Generating autoload files
   132 packages you are using are looking for funding.
   Use the `composer fund` command to find out more!
   No security vulnerability advisories found
   ```

1. Actualice `composer.json` para agregar [!DNL B2B] versión 1.4.0.

   ```bash
   composer require magento/extension-b2b=1.4.0
   ```

   **Salida de comando:**

   ```bash
   ./composer.json has been updated
   Running composer update magento/extension-b2b
   Loading composer repositories with package information
   Updating dependencies
   ...
   Generating autoload files
   132 packages you are using are looking for funding.
   Use the `composer fund` command to find out more!
   No security vulnerability advisories found
   ```

1. Complete el proceso de instalación o actualización.

   * [Instalar [!DNL B2B] en la infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/b2b-module.html?lang=es)
   * [Instalar local](https://experienceleague.adobe.com/docs/commerce-admin/b2b/install.html?lang=es)
