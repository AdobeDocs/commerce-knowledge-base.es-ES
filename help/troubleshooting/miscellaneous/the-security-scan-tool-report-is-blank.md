---
title: El informe Herramienta de exploración de seguridad está en blanco
description: Este artículo proporciona una solución para el problema en el que la Herramienta de exploración de seguridad muestra una página en blanco en lugar del informe real. Para resolverlo, es posible que tenga que añadir las direcciones IP utilizadas por la herramienta a la Lista de permitidos del cortafuegos.
exl-id: e5f7f8c6-2dd3-44e3-8d19-f1f38d06dd6c
feature: Compliance, Security
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# El informe Herramienta de exploración de seguridad está en blanco

Este artículo proporciona una solución para el problema en el que la Herramienta de exploración de seguridad muestra una página en blanco en lugar del informe real. Para resolverlo, es posible que tenga que añadir las direcciones IP utilizadas por la herramienta a la Lista de permitidos del cortafuegos.

## Productos y versiones afectados:

* Adobe Commerce (todos los métodos de implementación) y Magento Open Source, Todas las versiones

## Problema

<u>Pasos a seguir</u>:

1. Configure la Herramienta de análisis de seguridad para comprobar el sitio web, tal como se describe en [Análisis de seguridad](https://docs.magento.com/m2/ee/user_guide/magento/security-scan.html) en nuestra guía del usuario.
1. En la columna Acciones, seleccione **Ejecutar análisis**.

<u>Resultados esperados</u>:

Vea la notificación de finalización del informe y la capacidad de abrirlo.

<u>Resultados reales</u>:

No hay notificaciones ni informes disponibles.

## Causa

Es posible que este problema aparezca porque Security Scan Tool no pudo llegar a su sitio web. Esto significa que el sitio web no está operativo y no se puede acceder a él, o que se está bloqueando el Analizador de seguridad.

## Solución

Intente abrir el sitio web.

* Si la página se carga correctamente, es posible que tenga que agregar las direcciones IP utilizadas por las herramientas de análisis de seguridad a la Lista de permitidos del cortafuegos. Se utilizan las siguientes direcciones IP: 52.87.98.44, 34.196.167.176, 3.218.25.102 en los puertos 80 y 443.
* Si el sitio no se carga y devuelve el *&quot;Se ha producido un error al procesar su solicitud&quot;* mensaje, compruebe si hay posibles errores en el sitio web.

## Lectura relacionada

* [Puesta en marcha e inicio](https://devdocs.magento.com/guides/v2.3/cloud/live/live.html?_ga=2.73579601.273749082.1559572284-888339099.1547722854#security-scan) en nuestra documentación para desarrolladores.
* [Análisis de seguridad](https://docs.magento.com/m2/ee/user_guide/magento/security-scan.html) en nuestra guía del usuario.
