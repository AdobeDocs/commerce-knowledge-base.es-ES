---
title: Google Analytics se desactiva después de la implementación
description: En este tema se describe una solución a un problema típico que podría experimentar con Google Analytics durante la implementación.
exl-id: ecf6a277-2dfa-45cf-b86f-9a27f39017f4
feature: Build, Deploy, Variables
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
subfeature_v2:
  - id: adedf3b3-e153-47a3-ae73-b5d65067b544
    internal-label: Build system
  - id: 2191e157-828a-5358-ad69-ebcaa8402915
    internal-label: Variables
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%
---
# Google Analytics se desactiva después de la implementación

En este tema se describe una solución a un problema típico que podría experimentar con Google Analytics durante la implementación.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, todas las versiones

## Problema

Al implementar el código en todos los entornos, los scripts de compilación e implementación comprueban que la rama `master/production/staging` está implementada para mantener Google Analytics habilitado. Al implementar ramas de desarrollo (o secundarias) de entornos maestros a desarrolladores (integración), el script de implementación deshabilita Google Analytics.

## Causa

Se trata de una función diseñada para garantizar que los datos y las interacciones del desarrollador no se envíen a Google Analytics ni sean rastreados por esta.

## Solución

Si desea que Google Analytics siempre esté habilitado, establezca la variable de implementación `ENABLE_GOOGLE_ANALYTICS = true`, tal como se describe en [Implementar variables](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#enable_google_analytics) en nuestra documentación para desarrolladores.

>[!NOTE]
>
>Somos conscientes de que este artículo aún puede contener términos de software estándar en la industria que algunos pueden encontrar racistas, sexistas u opresivos y que pueden hacer que el lector se sienta herido, traumatizado o no deseado. Adobe está trabajando para eliminar estos términos de nuestro código, documentación y experiencias de usuario.
