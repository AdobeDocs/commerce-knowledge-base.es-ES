---
title: 'Solicitud de mejora del entorno de integración: Pro y Starter'
description: Si es cliente de Adobe Commerce en la infraestructura en la nube, planifica la arquitectura Pro y actualmente utiliza los entornos de integración de tamaño estándar, o si es cliente de Adobe Commerce en la infraestructura en la nube, planifica la arquitectura del plan inicial y actualmente utiliza el entorno de ensayo de tamaño estándar y desea obtener más potencia, puede solicitar una actualización a los entornos de integración mejorados, que proporcionan aproximadamente cuatro veces el rendimiento. Este artículo separa las instrucciones para los clientes de Pro de los clientes de Starter.
exl-id: c49b049b-efb8-412f-b27d-a89f8a758d85
feature: Integration
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 0%

---

# Solicitud de mejora del entorno de integración: Pro y Starter

Si es cliente de Adobe Commerce en la infraestructura en la nube, planifica la arquitectura Pro y actualmente utiliza los entornos de integración de tamaño estándar, o si es cliente de Adobe Commerce en la infraestructura en la nube, planifica la arquitectura del plan inicial y actualmente utiliza el entorno de ensayo de tamaño estándar y desea obtener más potencia, puede solicitar una actualización a los entornos de integración mejorados, que proporcionan aproximadamente cuatro veces el rendimiento. Este artículo separa las instrucciones para los clientes de Pro de los clientes de Starter.

>[!NOTE]
>
> Es posible que la actualización a la integración mejorada no solucione todos los problemas de rendimiento, ya que dependería del total de requisitos de recursos de la instalación, incluidas las integraciones o personalizaciones de terceros.
>
> También debe asegurarse de seguir las prácticas recomendadas para obtener el mejor rendimiento en el entorno de integración e incluso de que esa no sea una solución completa. Consulte la siguiente documentación para obtener instrucciones: [Arquitectura profesional](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment) y [Arquitectura inicial](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment) en la Guía de infraestructura de Commerce en la nube.

## Pro

1. Si está en Pro, para actualizar debe reducir el número de ramas de integración a dos (**la rama de integración principal está incluida en el total**). **Nota: no cuente la rama principal en este total. La rama principal no se considera una rama de integración.** Siga los pasos de [Administrar ramas con la consola en la nube](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html) en nuestra documentación para desarrolladores.
1. El comerciante necesita [enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) solicitando una actualización a los entornos de integración mejorada, utilizando el motivo de contacto &quot;*Solicitar un cambio de configuración en la nube*&quot;.
1. El equipo de ingeniería de clientes de Adobe confirma el número de entornos de integración e inicia el cambio.
1. Se notificará al comerciante en el ticket cuando se complete la actualización.
1. El comerciante vuelve a implementar los entornos de integración. Siga los pasos de [Combinar una rama](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches#merge-a-branch) en nuestra documentación para desarrolladores. *Nota*: la implementación se produce automáticamente cuando se ejecuta: <pre>git push origin <branch-name></pre>

El aumento del rendimiento indica una actualización correcta a los entornos de integración mejorados.

**Notas**:

* El tamaño estándar y el tamaño mejorado son los únicos dos tamaños disponibles.
* Todos los entornos de integración de una tienda determinada son del mismo tamaño; no se pueden cambiar de tamaño de forma independiente.
* Si necesita más de dos de los entornos de integración mejorados, póngase en contacto con su equipo de cuenta de Adobe.

## Starter

1. Los planes de inicio no pueden tener ninguna rama de integración: los comerciantes deben eliminar los entornos de integración y dejar solo el entorno de ensayo. Siga los pasos de [Administrar ramas con Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html) en nuestra documentación para desarrolladores. El número de entornos disponibles se reducirá para permitir un máximo de un entorno de integración.
1. El comerciante debe [enviar un vale de soporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) solicitando una actualización a los entornos de integración mejorada, por el motivo de contacto *&quot;Solicitar un cambio de configuración de nube&quot;* - **su entorno de ensayo es un entorno de integración con nombre**.
1. El equipo de ingeniería de clientes de Adobe confirma el número de entornos de integración e inicia el cambio.
1. Se notificará al comerciante en el ticket cuando se complete la actualización.
1. El comerciante vuelve a implementar los entornos de integración. Siga los pasos de [Combinar una rama](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches#merge-a-branch) en nuestra documentación para desarrolladores. *Nota*: la implementación se produce automáticamente cuando se ejecuta: <pre>git push origin <branch-name></pre>

El aumento del rendimiento indica una actualización correcta a los entornos de integración mejorados.

**Notas**:

* El tamaño estándar y el tamaño mejorado son los únicos dos tamaños disponibles.
* Todos los entornos de integración de una tienda determinada son del mismo tamaño; no se pueden cambiar de tamaño de forma independiente.
* Si necesita entornos de integración más allá del ensayo, consulte con su equipo de cuenta de Adobe.
* En caso de que la compra se realice después del 17 de septiembre de 2020, esta mejora no será aplicable debido a los entornos de integración ampliados.
