---
title: Los Google Analytics se desactivan después de la implementación
description: En este tema se describe una solución a un problema típico que podría experimentar con los Google Analytics durante la implementación.
exl-id: ecf6a277-2dfa-45cf-b86f-9a27f39017f4
feature: Build, Deploy, Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# Los Google Analytics se desactivan después de la implementación

En este tema se describe una solución a un problema típico que podría experimentar con los Google Analytics durante la implementación.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, todas las versiones

## Problema

Al implementar el código en todos los entornos, los scripts de compilación e implementación comprueban que la rama `master/production/staging` está implementada para mantener los Google Analytics habilitados. Al implementar ramas de desarrollo (o secundarias) de entornos maestros a desarrolladores (integración), el script de implementación deshabilita los Google Analytics.

## Causa

Se trata de una función diseñada para garantizar que los datos del desarrollador y las interacciones no se envíen a los Google Analytics ni los rastreen.

## Solución

Si desea que los Google Analytics estén siempre habilitados, establezca la variable de implementación `ENABLE_GOOGLE_ANALYTICS = true`, tal como se describe en [Implementar variables](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#enable_google_analytics) en nuestra documentación para desarrolladores.

>[!NOTE]
>
>Somos conscientes de que este artículo aún puede contener términos de software estándar en la industria que algunos pueden encontrar racistas, sexistas u opresivos y que pueden hacer que el lector se sienta herido, traumatizado o no deseado. El Adobe de está trabajando para eliminar estos términos de nuestro código, documentación y experiencias de usuario.
