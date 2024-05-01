---
title: "MDVA-30102: La caché de Redis se está llenando"
description: El parche MDVA-30102 soluciona el problema de que la caché de Redis se llene y genere errores, lo que provoca problemas con las páginas de lista de productos (PLP) y las páginas de detalles de producto (PDP), como la falta de productos. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.6.
exl-id: 34772296-8c93-471c-b5ad-6815adb78ca6
feature: Cache, Categories, Services
role: Admin
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---

# MDVA-30102: La caché de Redis se está llenando

El parche MDVA-30102 soluciona el problema de que la caché de Redis se llene y genere errores, lo que provoca problemas con las páginas de lista de productos (PLP) y las páginas de detalles de producto (PDP), como la falta de productos. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.6 está instalado.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce en infraestructura en la nube 2.3.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.2 - 2.4.1-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La caché de Redis se está llenando y el asignado `maxmemory` parece ser insuficiente. La caché de diseño no tenía TTL y no se desalojó, lo que provocó el crecimiento de la caché y la expulsión de otras claves en Redis. Como resultado, toda la memoria Redis se asignó a la caché de diseño.

<u>Requisitos previos</u>:

* El usuario debe estar en Adobe Commerce 2.4 y tener 100 000 productos simples (el tipo de producto no importa) y 50 categorías.
* La caché de Redis debe configurarse según los pasos indicados en [Guía de configuración de Adobe Commerce > Uso de Redis para la página de Adobe Commerce y la caché predeterminada](https://devdocs.magento.com/guides/v2.4/config-guide/redis/redis-pg-cache.html#example-command) en nuestra documentación para desarrolladores.

<u>Pasos a seguir</u>:

1. Examine todos los PDP y PLP. Puede utilizar [OWASP ZAP](https://www.zaproxy.org/) para rastrear el sitio.
1. Observe el uso de la memoria Redis.
1. Compruebe también la configuración actual y la memoria utilizada. Ejecute el siguiente comando en la CLI. Comprueba la memoria utilizada, la memoria máxima, las claves desalojadas y el tiempo de activación de Redis en días:

```
redis-cli -p REDIS_PORT -h REDIS_HOST info | egrep --color "(role|used_memory_peak|maxmemory|evicted_keys|uptime_in_days)"
```

<u>Resultados esperados</u>:

La caché de Redis no debería crecer rápidamente.

<u>Resultados reales</u>:

La caché de Redis crece hasta ~5 GB. Hay un límite máximo de 8 GB de memoria Redis, por lo que si tiene 1 M de productos, se quedará sin memoria muy rápidamente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
