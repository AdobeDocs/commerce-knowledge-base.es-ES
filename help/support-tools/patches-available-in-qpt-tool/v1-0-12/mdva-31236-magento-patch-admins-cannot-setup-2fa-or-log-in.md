---
title: "MDVA-31236: los administradores no pueden configurar 2FA ni iniciar sesión"
description: El parche MDVA-31236 corrige el problema en el que los usuarios administradores de Commerce con acceso a recursos personalizados no pueden configurar la [autenticación de doble factor (2FA)](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html) ni iniciar sesión. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12.
exl-id: b75d7a19-3c17-4389-b359-7aeeb8797539
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# MDVA-31236: los administradores no pueden configurar 2FA ni iniciar sesión

El parche MDVA-31236 corrige el problema en el que los usuarios administradores de Commerce con acceso a recursos personalizados no pueden configurar [autenticación de doble factor (2FA)](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html) o inicie sesión. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 está instalado.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:** Adobe Commerce en la infraestructura en la nube 2.4.0.

**Compatible con las versiones de Adobe Commerce:** Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.4.0-2.4.1.

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios sin privilegios de administrador no pueden configurar actualmente su acceso personal de 2FA. 2FA tal como se implementa en Adobe Commerce incluye dos funciones ACL. Un rol afecta a la configuración global del sistema y sólo es necesario cuando se configura el sistema. La segunda función ACL afecta a las cuentas 2FA de usuario individual. Un usuario administrador debe configurar este segundo tipo de ACL 2FA.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sección.
