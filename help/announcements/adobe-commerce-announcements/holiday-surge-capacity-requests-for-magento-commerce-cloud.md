---
title: Solicitudes de capacidad de Holiday Surge para Adobe Commerce en nuestra infraestructura en la nube
description: Durante la temporada alta de ventas de las fiestas (aproximadamente de mediados de noviembre a mediados de enero), Adobe recomienda que todos los comerciantes de Adobe Commerce alojados en nuestra infraestructura en la nube se preparen para un mayor tráfico.
exl-id: 9d6910bf-30bc-4117-bf7f-a0316f9506b5
feature: Cloud, Paas
role: Admin
source-git-commit: dfd3f788f42677b631ffb5b3153a1c79c2cc1ca3
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Solicitudes de capacidad de Holiday Surge para Adobe Commerce en nuestra infraestructura en la nube

Durante la temporada alta de ventas de las fiestas (aproximadamente de mediados de noviembre a mediados de enero), Adobe recomienda que todos los comerciantes de Adobe Commerce alojados en nuestra infraestructura en la nube se preparen para un mayor tráfico.

**Planificación y estimación del tráfico**

Recomendamos que todos los comerciantes de Adobe Commerce usen nuestra infraestructura en la nube [utilice este conjunto de recomendaciones sobre cómo calcular el tráfico en temporada alta](https://business.adobe.com/blog/how-to/the-5-ps-of-peak-season-performance-a-guide-to-preparing-your-infrastructure-for-high-traffic) para la temporada alta de ventas de vacaciones cada año.

Una vez que haya completado la estimación recomendada, si su equipo ha identificado fechas en las que cree que necesitará capacidad adicional, continúe con el siguiente paso para obtener información sobre cómo solicitar capacidad de sobrecarga.

**Ver el historial de las conversiones**

Puede ver el historial de los cambios de tamaño solicitados en su [Portal de proyectos (IU de incorporación)](https://devdocs.magento.com/cloud/onboarding/onboarding-tasks.html), en **Proyecto** > **Servicios** > **Seguimiento del uso de CPU**.
La siguiente información está disponible para cada solicitud de cambio de tamaño:

* **Fecha de inicio del tamaño**: fecha de la solicitud de actualización.
* **Fecha de finalización de tamaño**: fecha en la que se devolvió el clúster al tamaño anterior.
* **Tamaño de vCPU**: el tamaño del clúster después del cambio de tamaño.
* **Uso de días**: durante cuántos días permaneció actualizado el clúster.
* **vCPU de período**: cambió el tamaño de vCPU por el número de días que se utilizó. (por ejemplo, el tamaño de vCPU 192 por 25 días equivale a 4.800).

**Solicitando capacidad de sobretensión**

Los comerciantes de Adobe Commerce que utilicen nuestra infraestructura en la nube y que prevean la necesidad de capacidad adicional durante la temporada de vacaciones deberían [Enviar un ticket de soporte de capacidad de Surge](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize.html) a través de nuestro [Centro de ayuda](/help/overview.md), indicando las fechas y las necesidades de capacidad esperadas dentro del ticket. Tenga en cuenta que el aumento de la capacidad requerirá el uso de la capacidad adicional con licencia.

**Recomendamos enviar estas entradas con al menos 48 horas laborables de antelación con respecto al momento en que se necesita la capacidad; y además recomendamos que las solicitudes para el período Black Friday / Cyber Monday se realicen con la mayor anticipación posible, ya que la capacidad durante este período es limitada.**


**¿Más ayuda?**

¿Necesita más orientación para prepararse para el tráfico de temporada alta? Los comerciantes de Adobe Commerce en nuestra infraestructura en la nube pueden ponerse en contacto con su equipo de cuenta de Adobe para obtener ayuda, estrategia y consejos de planificación para prepararse para una temporada alta exitosa. También recomendamos consultar el [Blog de Magento](https://magento.com/blog) para obtener sugerencias de estrategia durante todo el año.

## Recursos para revisar su capacidad

En nuestra base de conocimiento de soporte:

* [Cálculo de asignación de CPU para Adobe Commerce en la nube](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
* [Compruebe si se necesita convertir para las instancias del host para Adobe Commerce en la nube](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
* [Compruebe la configuración de CPU del host para Adobe Commerce en la nube](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* [Identificar y medir las interrupciones del servicio de Adobe Commerce en la nube](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html)
