---
title: Instale los parches más recientes para solucionar los problemas de Adobe Commerce Redis
description: Este artículo proporciona información sobre los últimos parches relacionados con Redis disponibles en el paquete [Adobe Commerce on cloud Infrastructure Patches](https://devdocs.magento.com/cloud/project/project-patch.html).
exl-id: 0335bc11-f679-4629-b4e7-6a0e68c3ae44
feature: Cache, Install, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Instale los parches más recientes para solucionar los problemas de Adobe Commerce Redis

Este artículo proporciona información sobre los últimos parches relacionados con Redis disponibles en [Parches de Adobe Commerce en la infraestructura en la nube](https://devdocs.magento.com/cloud/project/project-patch.html) paquete.

## Productos y versiones afectados

Adobe Commerce en infraestructura en la nube 2.3.3, 2.3.4

## Problema

El consumo adicional de CPU y memoria por parte de Redis podría disminuir el rendimiento de Adobe Commerce y, por lo tanto, el rendimiento general de su sitio web.

## Solución

Aplique los parches más recientes proporcionados por Adobe Commerce en el paquete de parches de la infraestructura en la nube. Para obtener instrucciones detalladas, consulte [Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

Los últimos parches Redis del paquete de parches de Adobe Commerce en la infraestructura en la nube contribuyen a lo siguiente:

* reducir el tamaño de la comunicación de red para Redis
* corregir las condiciones de carrera que llevan a un consumo de memoria adicional
* cambio del adaptador de caché para cubrir casos de desalojo
* reducir el consumo de CPU de Redis

Adobe Commerce también recomienda actualizar a Redis 5 si ejecuta Adobe Commerce en la infraestructura en la nube 2.3.3 o superior.
