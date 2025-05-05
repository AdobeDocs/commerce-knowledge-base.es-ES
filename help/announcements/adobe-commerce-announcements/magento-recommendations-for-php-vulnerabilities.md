---
title: Vulnerabilidades de Adobe Commerce Recommendations para PHP
description: El 3 de septiembre, el Centro de Análisis e Intercambio de Información Multiestatal (MS-ISAC) emitió una alerta relacionada con múltiples vulnerabilidades que podrían permitir la ejecución de código arbitrario y una recomendación de que todos los sitios que utilicen PHP deben actualizar a la última versión de PHP lo antes posible ([alerta completa está disponible aquí](https://www.cisecurity.org/advisory/multiple-vulnerabilities-in-php-could-allow-for-arbitrary-code-execution_2019-087/)).
exl-id: 0bc7caab-0b89-463a-a7f2-a7c92df9f84e
feature: Compliance, Recommendations
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---

# Vulnerabilidades de Adobe Commerce Recommendations para PHP

El 3 de setiembre, el Centro de Análisis e Intercambio de Información de Varios Estados (MS-ISAC) emitió una alerta relacionada con múltiples vulnerabilidades que podrían permitir la ejecución de código arbitrario y una recomendación de que todos los sitios que usen PHP deben actualizar a la última versión de PHP lo antes posible ([alerta completa está disponible aquí](https://www.cisecurity.org/advisory/multiple-vulnerabilities-in-php-could-allow-for-arbitrary-code-execution_2019-087/)).

>[!WARNING]
>
>En Adobe Commerce sobre la infraestructura en la nube, tenga en cuenta que las actualizaciones de servicios no se pueden insertar en el entorno de producción sin un aviso de 48 horas laborables a nuestro equipo de infraestructura. Esto es necesario, ya que tenemos que asegurarnos de tener un ingeniero de asistencia técnica de infraestructura disponible para actualizar la configuración dentro de un periodo de tiempo deseado con un tiempo de inactividad mínimo en el entorno de producción. Así que 48 horas antes de que sus cambios deban estar en producción [envíe un ticket de soporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) detallando su actualización de servicio requerida e indicando la hora en que desea que comience el proceso de actualización.

Siga leyendo para ver los impactos y los pasos de los sitios de Adobe Commerce:

**Adobe Commerce alojado en nuestro producto en la nube**

Si utiliza Adobe Commerce en una infraestructura en la nube, trabaje con su equipo tecnológico para volver a implementar Adobe Commerce a partir de cualquier momento\* para aprovechar la actualización. Recomendamos que los comerciantes completen esta reimplementación antes del 30 de septiembre para evitar problemas de cumplimiento de PCI que puedan entrar en vigor como resultado de estas vulnerabilidades a finales de mes.

Notas adicionales sobre la reimplementación del sitio en la nube para esta actualización:

* Si su sitio sigue usando la versión 7.0 de PHP, primero deberá actualizar a una versión compatible de PHP antes de volver a implementarlo para aprovechar estas actualizaciones de seguridad.
* Para 2.1.x/2.2.x, se puede encontrar más información sobre la actualización de PHP [aquí](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html?lang=es).

\* *Las versiones anteriores de este artículo y nuestros mensajes se publicaron el 19 de septiembre, pero nuestros equipos han finalizado su trabajo antes de lo previsto.*

**Adobe Commerce en todas las demás soluciones de alojamiento**

Dado que Adobe Commerce se basa en PHP, recomendamos que todos los comerciantes que utilicen Adobe Commerce revisen las actualizaciones necesarias para PHP con su proveedor de alojamiento. También recomendamos que los comerciantes completen esta revisión y cualquier actualización antes del 30 de septiembre para evitar problemas de cumplimiento de PCI que puedan entrar en vigor como resultado de estas vulnerabilidades a finales de mes.

Tenga en cuenta algunos detalles adicionales para Adobe Commerce en otras soluciones de alojamiento:

* Las versiones 2.0 o 1.x de Adobe Commerce que usan versiones de PHP anteriores a la 7.1 o superiores no tienen parches oficiales de PHP disponibles. La ruta recomendada es actualizar PHP a una versión compatible de PHP.

Según la alerta, los parches recomendados para esta vulnerabilidad incluyen:

* PHP 7.1: [https://www.php.net/ChangeLog-7.php\#7.1.32](https://www.php.net/ChangeLog-7.php#7.1.32)
* PHP 7.2: [https://www.php.net/ChangeLog-7.php\#7.2.22](https://www.php.net/ChangeLog-7.php#7.2.22)
* PHP 7.3: [https://www.php.net/ChangeLog-7.php\#7.3.9](https://www.php.net/ChangeLog-7.php#7.3.9)

Si desea obtener más información sobre PHP y las versiones recientes, visite el sitio de [PHP](https://www.php.net/). Y si tiene preguntas o desea obtener más información sobre las prácticas recomendadas de seguridad, consulte nuestra [Guía de prácticas recomendadas de seguridad](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf).
