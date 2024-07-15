---
title: "Alertas administradas en Adobe Commerce: Alerta de advertencia de memoria Redis"
description: 'Este artículo proporciona pasos para solucionar problemas cuando recibe una alerta de advertencia de Redis para Adobe Commerce en New Relic. Se requiere una acción inmediata para resolver el problema. La alerta tendrá el siguiente aspecto, según el canal de notificación de alerta que haya seleccionado:'
exl-id: b7867a42-3817-4cb4-93cf-d69acee33a41
feature: Categories, Marketing Tools, Observability, Services, Support, Tools and External Services, Variables
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# Alertas administradas en Adobe Commerce: alerta de advertencia de memoria Redis

Este artículo proporciona pasos para solucionar problemas cuando recibe una alerta de advertencia de Redis para Adobe Commerce en New Relic. Se requiere una acción inmediata para resolver el problema. La alerta tendrá el siguiente aspecto, según el canal de notificación de alerta que haya seleccionado:

![new_relic_redis_memory_warning.png](assets/new_relic_redis_memory_warning.png)

## Productos y versiones afectados

Todas las versiones de Adobe Commerce en la infraestructura en la nube planifican la arquitectura Pro.

## Problema

Recibirá una alerta en New Relic si se ha registrado en [Alertas administradas para Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) y se han sobrepasado uno o más de los umbrales de alerta. Estas alertas fueron desarrolladas por el Adobe para ofrecer a los comerciantes un conjunto estándar de alertas mediante perspectivas de Soporte e Ingeniería.

**<u>Hacer!</u>**

* Se recomienda cancelar cualquier implementación programada hasta que se borre esta alerta.
* Si su sitio no responde o deja de responder por completo, ponga inmediatamente el sitio en modo de mantenimiento. Para ver los pasos, consulte [Guía de instalación > Habilitar o deshabilitar el modo de mantenimiento](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#enable-or-disable-maintenance-mode-1) en nuestra Guía de instalación.
* Asegúrese de añadir su IP a la lista de direcciones IP exentas para asegurarse de que aún puede acceder al sitio para solucionar problemas. Para ver los pasos, consulte [Mantener la lista de direcciones IP exentas](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#maintain-the-list-of-exempt-ip-addresses) en nuestra Guía de instalación.

**<u>¡No!</u>**

* Inicie campañas de marketing adicionales que puedan llevar vistas de página adicionales al sitio.
* Ejecute indexadores o crons adicionales que puedan causar estrés adicional en la CPU o el disco.
* Realice cualquier tarea administrativa importante (es decir, una acción importante en el administrador de Commerce, como importaciones/exportaciones de datos, vaciado de medios, guardado de categorías con un gran número de productos asignados y actualizaciones masivas).
* Borre la caché.

## Solución

Siga estos pasos para identificar y solucionar los problemas de la causa.

1. Compruebe si la memoria usada de Redis aumenta o disminuye en [one.newrelic.com](https://login.newrelic.com/login) > **Infraestructura** > **Servicios de terceros**, seleccione el panel de Redis. Si es estable o aumenta, [envíe un vale de soporte técnico](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para que se actualice el clúster, o bien aumente el límite de `maxmemory` al siguiente nivel.
1. Si no puede identificar la causa del aumento del consumo de memoria de Redis, revise las tendencias recientes para identificar los problemas con las implementaciones de código o los cambios de configuración recientes (por ejemplo, nuevos grupos de clientes y cambios grandes en el catálogo). Se recomienda revisar los últimos siete días de actividad para cualquier correlación en implementaciones o cambios de código.
1. Compruebe si hay extensiones de terceros con comportamiento incorrecto:
   * Intente encontrar una correlación con las extensiones de terceros instaladas recientemente y la hora en que comenzó el problema.
   * Revise las extensiones que podrían afectar a la caché de Adobe Commerce y hacer que esta crezca rápidamente. Por ejemplo, los bloques de diseño personalizados, la anulación de la funcionalidad de la caché y el almacenamiento de grandes cantidades de datos en la caché.
1. Si no hay evidencia de extensiones mal comportadas, [instale los parches más recientes para corregir los problemas de Redis para Adobe Commerce en la infraestructura en la nube](/help/troubleshooting/miscellaneous/install-latest-patches-to-fix-magento-redis-issues.md). Si los pasos anteriores no le ayudan a identificar o solucionar el origen del problema, considere la posibilidad de habilitar la caché L2 para reducir el tráfico de red entre la aplicación y Redis. Para obtener información general sobre qué es la caché L2, consulte [Almacenamiento en caché L2 en la aplicación Adobe Commerce](/docs/commerce-operations/configuration-guide/cache/level-two-cache.html) en nuestra Guía de configuración. Para habilitar la caché L2 para la infraestructura en la nube, intente lo siguiente:
   * Actualice las herramientas de ECE si es inferior a la versión 2002.1.2.
   * Configurar la caché L2 mediante [Usar la variable REDIS\_BACKEND](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) y actualizar el archivo `.magento.env.yaml`:

   ```yaml
   stage:
      deploy:
          REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```
