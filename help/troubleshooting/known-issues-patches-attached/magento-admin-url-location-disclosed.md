---
title: Ubicación de URL de administrador de Adobe Commerce revelada
description: Este artículo proporciona un parche para el problema de seguridad de Adobe Commerce en el que se puede revelar la ubicación URL del Panel de administración. Conocer la ubicación de la URL podría facilitar la automatización de los ataques.
exl-id: fe147ad5-6019-46c1-b48c-6b957b6e1582
feature: Admin Workspace
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# Ubicación de URL de administrador de Adobe Commerce revelada

Este artículo proporciona un parche para el problema de seguridad de Adobe Commerce en el que se puede revelar la ubicación URL del Panel de administración. Conocer la ubicación de la URL podría facilitar la automatización de los ataques.

## Productos y versiones afectados

* Adobe Commerce en infraestructura en la nube 2.X.X
* Adobe Commerce local 2.X.X
* Magento Open Source 2.X.X

## Problema

Se ha detectado un problema en Magento Open Source y Adobe Commerce que puede utilizarse para revelar la ubicación URL del panel de administración. Aunque actualmente no hay motivos para creer que este problema pueda implicar un compromiso directo, conocer la ubicación de la URL podría facilitar la automatización de los ataques.

## Solución

Para solucionar el problema, aplique el parche adjunto a este artículo. Para descargarlo, haga clic en el siguiente vínculo:

* Descargar [PRODSECBUG-2432\_EE\_2.1.17\_composer.patch](assets/PRODSECBUG-2432_EE_2.1.17_composer.patch.zip) para las versiones 2.1.13-2.1.17, Adobe Commerce, Magento Open Source
* Descargar [PRODSECBUG-2432\_EE\_2.2.8\_composer.patch](assets/PRODSECBUG-2432_EE_2.2.8_composer.patch.zip): para las versiones 2.2.0-2.2.8, todas las ediciones
* Descargar [PRODSECBUG-2432\_EE\_2.3.1\_composer.patch](assets/PRODSECBUG-2432_EE_2.3.1_composer.patch.zip): para las versiones 2.3.0-2.3.1, todas las ediciones

Si no ve un parche para su producto/versión, actualice a la última versión de seguridad y aplique el parche.

El Adobe recomienda encarecidamente que se aplique el parche lo antes posible, incluso si no ha experimentado ningún síntoma de una crisis.

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obtener instrucciones.

## Otras recomendaciones de seguridad

El Adobe también recomienda encarecidamente que los comerciantes implementen herramientas para proteger su panel de administración, incluida la autenticación de doble factor, VPN, Inclusión en la lista de permitidos IP y más. Para obtener información detallada, consulte los siguientes blogs y documentación:

* [5 Acciones inmediatas a Protect contra ataques por fuerza bruta](https://magento.com/security/best-practices/5-immediate-actions-protect-against-brute-force-attacks)
* [Protect: su contraseña de instalación de Magento que adivina la nueva actualización](https://magento.com/security/best-practices/protect-your-magento-installation-password-guessing-new-update)
* [Prácticas recomendadas de seguridad](https://magento.com/security/best-practices/security-best-practices)
* Agregar y configurar la autenticación de doble factor en Adobe Commerce para [2.4.x](https://experienceleague.adobe.com/es/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication)
