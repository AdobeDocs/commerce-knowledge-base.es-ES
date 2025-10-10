---
title: Cómo solicitar la actualización temporal de Adobe Commerce en la infraestructura en la nube
description: Si su organización planea un evento en línea en el que se espera un tráfico elevado, o si de repente encuentra que su sitio está pasando por un evento de tráfico elevado, puede presentar un [vale de soporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para solicitar capacidad adicional temporal en la nube para su Adobe Commerce en el almacén de infraestructura en la nube.
exl-id: 561e2bdd-718a-45c1-8b6c-a0e3a6c8ad04
feature: Cloud, Iaas
source-git-commit: e59335b67e1f33e138e34cab93ce593836d14b48
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Cómo solicitar la actualización temporal de Adobe Commerce en la infraestructura en la nube

Si su organización planea un evento en línea en el que se espera un tráfico elevado o si de repente encuentra que su sitio está pasando por un evento de tráfico elevado, puede presentar un [vale de soporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para solicitar capacidad adicional temporal en la nube para su Adobe Commerce en el almacén de infraestructura en la nube.

>[!NOTE]
>
>Se requiere un aviso de 48 horas hábiles para las solicitudes de ampliación que no sean de emergencia. Las actualizaciones para campañas promocionales no se consideran emergencias a menos que el sitio no funcione por completo o reciba un tráfico mucho mayor de lo previsto y el rendimiento se haya degradado gravemente.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, todas [versiones compatibles](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Cómo identificar eventos de alto tráfico

En las alertas de New Relic, puede utilizar condiciones de alerta de línea de base para definir umbrales que se ajusten al comportamiento de los datos.

Las alertas de línea de base son útiles para crear condiciones de alerta que:

* Notificarle únicamente cuando los datos se estén comportando de forma anormal.
* Se ajustan dinámicamente a los datos y tendencias cambiantes, incluidas las tendencias diarias o semanales.

Además, las alertas de línea de base funcionan bien con las aplicaciones nuevas cuando aún no tiene comportamientos conocidos.

Siga este vínculo para obtener más información acerca de New Relic [Detección de anomalías con inteligencia aplicada](https://docs.newrelic.com/docs/alerts-applied-intelligence/applied-intelligence/anomaly-detection/anomaly-detection-applied-intelligence/).

Si recibe una notificación de alerta que sugiere un evento de alto tráfico, tal vez tenga que considerar [enviar un vale de asistencia](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) para solicitar capacidad adicional. Siga los siguientes pasos.

## Monitorización del rendimiento del sitio

Adobe proporciona un conjunto de políticas de alerta de New Relic para Adobe Commerce en la infraestructura en la nube, la arquitectura de plan Pro y Adobe Commerce en la infraestructura en la nube, la arquitectura de plan inicial, los entornos de producción para realizar un seguimiento de las siguientes métricas clave de rendimiento:

* [Puntuación Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)
* Tasa de error
* Espacio en disco (solo disponible en entornos de producción con arquitectura Pro)

Estas políticas, basadas en las prácticas recomendadas del sector, establecen umbrales para las condiciones críticas y de advertencia que afectan al rendimiento. Cuando el sitio experimenta un problema de infraestructura o aplicación que déclencheur un umbral de alerta, New Relic envía notificaciones de alerta para que pueda solucionarlo de forma proactiva. Para utilizar estas directivas, debe configurar los canales de notificación para recibir los mensajes de alerta.

Siga este enlace para aprender a [configurar alertas basadas en el rendimiento](/docs/commerce-cloud-service/user-guide/monitor/new-relic.html#monitor-performance-with-managed-alerts).

## Pasos para solicitar un aumento temporal

Para solicitar capacidad adicional en la nube, envía un [vale de soporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) en el Centro de soporte de Adobe Commerce con la siguiente información:

>[!NOTE]
>
>La opción *Solicitud de Marejada de Vacaciones* es solo una opción entre octubre y diciembre.

1. Seleccione el producto [!DNL Adobe Commerce] para el que necesita asistencia:
   * [!DNL Commerce Cloud]
   * [!DNL Commerce on Managed Service]

1. Rellene los campos siguientes:
   * **[!UICONTROL Case Title]**
   * **[!UICONTROL Case Description]** *(asegúrese de que estos describan claramente el problema y el contexto)*

1. Seleccione *Solicitud de cambio de infraestructura* en el menú desplegable **[!UICONTROL Issue Reason]**.

1. Elija **[!UICONTROL Environment]** en el menú desplegable.

1. Seleccione el(la) **[!UICONTROL Product Version]** apropiado(a) del menú desplegable.

1. Elija *Cambio de tamaño del proyecto en la nube (vCPU)* del menú desplegable **[!UICONTROL Which Infra Change you would like to do today]**.

1. **Seleccionar[!UICONTROL Architecture]**:
   * *Arquitectura predeterminada:* Seleccione *Siguiente tamaño disponible* del menú desplegable **Seleccionar el tamaño**.
   * *Arquitectura a escala:* Si se selecciona, la pantalla cambia para mostrar dos campos adicionales:
      * *Tamaño del nodo web*
      * *Tamaño del nodo de servicio* *(introduzca los tamaños deseados para cada nodo)*

1. Escriba **[!UICONTROL From Date]** en formato UTC (fecha y hora).

1. Escriba **[!UICONTROL To Date]** en formato UTC (fecha y hora).

1. Proporcionar **[!UICONTROL Project URL]** *(se encuentra en https://accounts.magento.cloud/, normalmente en formato `https://[REGION].magento.cloud/projects/PROJECT_ID`)*

1. Escriba **[!UICONTROL Project ID]**.

1. Proporcionar **[!UICONTROL Affected URL]** *(debe comenzar con `http://` o `https://`.)*

1. Seleccione **[!UICONTROL Priority]**.

1. Seleccione **[!UICONTROL Business Impact]**.

1. Confirmar **[!UICONTROL Time Zone]** *(por ejemplo, `(UTC-5:00) Indiana (East)`)*

1. Escriba **[!UICONTROL Phone Number]** *(por ejemplo, `+12015550123`)*

1. Haga clic en **[!UICONTROL Submit]** para finalizar su caso de soporte.

>[!NOTE]
>
>Una vez programado el cambio, un sistema automatizado ajustará el tamaño de la instancia de la nube. Es posible que no reciba ninguna notificación de ticket cuando el procedimiento haya finalizado. Puede usar la herramienta Observación para Adobe Commerce para ver los tipos de instancia de AWS o Azure para [comprobar el cambio](/help/how-to/general/check-vcpu-using-observation-for-adobe-commerce.md).

## Ver el historial de las conversiones

Puede ver el historial de los cambios de tamaño solicitados solicitando la información a su **CSM (Customer Success Manager)**.
La siguiente información está disponible para cada solicitud de cambio de tamaño:

* **Fecha de inicio de tamaño**: fecha de la solicitud de cambio de tamaño.
* **Fecha de finalización de tamaño**: fecha en la que se devolvió el clúster al tamaño anterior.
* **Tamaño de vCPU**: el tamaño del clúster después del cambio de tamaño.
* **Uso de días**: durante cuántos días permaneció el clúster actualizado.
* **Period vCPU**: se cambió el tamaño de vCPU por el número de días que se usó. (por ejemplo, el tamaño de vCPU 192 por 25 días equivale a 4.800).


## Lectura relacionada

* Para obtener información, métodos y ejemplos sobre cómo medir y mejorar el rendimiento del sitio, consulte los siguientes artículos detallados en nuestra base de conocimiento de asistencia:
   * [Cálculo de asignación de CPU para Adobe Commerce en la nube](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
   * [Compruebe si se necesita convertir para las instancias del host para Adobe Commerce en la nube](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
   * [Compruebe la configuración de CPU del host para Adobe Commerce en la nube](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* Para obtener información sobre cómo identificar interrupciones, consulte [Identificar y medir interrupciones para Adobe Commerce en la nube](/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html) en nuestra base de conocimiento de soporte.
* Para obtener información sobre la mejora del rendimiento del sitio para evitar la necesidad de utilizar un aumento en la capacidad, consulte estos artículos en nuestra documentación para desarrolladores:
   * [Tamaño de imagen](/docs/commerce-admin/catalog/products/digital-assets/product-image-config.html#product-image-resizing)
   * [Almacenamiento en caché de página completa](/docs/commerce-admin/systems/tools/cache-management.html#full-page-caching)
   * [ECE-Tools](/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html)
