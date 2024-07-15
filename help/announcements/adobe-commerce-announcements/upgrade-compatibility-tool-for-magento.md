---
title: Actualización de la herramienta de compatibilidad 1.1.0 para Adobe Commerce
description: La herramienta de compatibilidad de actualización 1.1.0 es una herramienta de línea de comandos que compara una instancia personalizada de Adobe Commerce con una versión específica analizando todos los módulos y el código principal instalados en ella. Devuelve una lista de errores, problemas y advertencias críticos que deben solucionarse antes de actualizar a la última versión de Adobe Commerce.
exl-id: 312abc5a-1d6a-4f32-9929-a94f4962eddd
feature: Upgrade
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---

# Actualización de la herramienta de compatibilidad 1.1.0 para Adobe Commerce

La herramienta de compatibilidad de actualización 1.1.0 es una herramienta de línea de comandos que compara una instancia personalizada de Adobe Commerce con una versión específica analizando todos los módulos y el código principal instalados en ella. Devuelve una lista de errores, problemas y advertencias críticos que deben solucionarse antes de actualizar a la última versión de Adobe Commerce.

## ¿Qué novedades hay en UCT 1.1.0?

La herramienta de compatibilidad de actualización 1.1.0 introduce mejoras significativas, entre las que se incluyen:

* **Validar modificaciones de archivos principales**: el Adobe recomienda encarecidamente no personalizar el código de producto principal. Con esta versión, hemos añadido un punto de comprobación para que los clientes y socios identifiquen cualquier modificación del código principal para comprender el impacto de las modificaciones de forma temprana y rápida. Añadir esta herramienta al proceso de desarrollo ayudará a los socios y comerciantes a identificar los problemas de forma proactiva, evitando problemas durante futuras actualizaciones y reduciendo el coste total de propiedad (TCO).
* **Exportar el informe a un archivo JSON**: esta mejora se implementó tras los comentarios de la comunidad. Ahora, al ejecutar la herramienta, los detalles de todos los problemas identificados se exportan a un archivo JSON para que los usuarios puedan leer, compartir y administrar los resultados sin tener que volver a ejecutar la herramienta.
* **Validaciones de VBE mejoradas**: las VBE (extensiones agrupadas de proveedor) no forman parte del código principal de Adobe Commerce, pero se prueban y admiten en el Adobe. Con esta actualización, ahora validamos los VBE con el mismo método que usamos para el código principal. Esta mejora ayudará a los usuarios a comprender claramente los problemas relacionados con las personalizaciones y los códigos principales/VBE.
* **Proporcionar códigos de error**: Hemos introducido códigos de error para ayudar a los usuarios a identificar, comprender y resolver problemas durante una actualización. Los mensajes de error y advertencia proporcionan una descripción clara y una solución sugerida.
* **Posibilidad de enumerar solamente los problemas críticos**: con esto, los usuarios podrán centrarse solamente en aquellos problemas que son críticos y generarán problemas al actualizar.
* **Problemas Delta entre dos versiones**: con esta mejora propuesta por los miembros de nuestra comunidad, los usuarios de UCT podrán obtener un delta de los problemas entre dos versiones, lo que les permitirá centrarse únicamente en los nuevos problemas introducidos para la versión de destino que actualizarán.

## ¿Qué versiones puede comparar la herramienta?

Puede utilizar la herramienta para comparar cualquier versión de 2.x.

## ¿Quién puede utilizar la herramienta de compatibilidad de actualización 1.1.0?

Clientes de Adobe Commerce.

## Instalación de la herramienta de compatibilidad de actualización 1.1.0

Para ver los pasos de instalación, consulte Adobe Commerce: [Actualizar herramienta de compatibilidad > Instalar](https://devdocs.magento.com/upgrade-compatibility-tool/install.html) en nuestra documentación para desarrolladores. Para conocer los requisitos previos para usar la herramienta, consulte Adobe Commerce: [Actualizar la herramienta de compatibilidad](https://devdocs.magento.com/upgrade-compatibility-tool/prerequisites.html) en nuestra documentación para desarrolladores.

## ¿Cuál es el número que hay junto a cada número?

Esta es la referencia de mensaje de error que proporciona información sobre los errores que pueden producirse al ejecutar la herramienta de compatibilidad de actualización.

Los mensajes de error de la herramienta de compatibilidad de actualización se clasifican por nivel (problemas críticos, errores y advertencias) y tipo (código principal, código personalizado y esquemas de GraphQL). Cada tipo contiene la siguiente información:

* Código de error: identificador asignado por Adobe Commerce al mensaje de error.
* Descripción del error: Descripción que resume la causa del error.
* Error: acción sugerida: si corresponde, proporciona instrucciones para solucionar y resolver el error.
* Los códigos se enumeran y describen en la [página de referencia de mensaje de error](https://devdocs.magento.com/upgrade-compatibility-tool/errors.html).

## ¿Dónde puedo compartir comentarios sobre la herramienta?

Puedes contactar con el equipo de UCT en nuestro canal de Slack [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). Esperamos recibir sus comentarios y sugerencias para mejorar la herramienta.

## Lectura relacionada

* Blog de Adobe Commerce: [Presentación de la herramienta de compatibilidad de actualización (Alpha)](https://magento.com/blog/magento-news/introducing-upgrade-compatibility-tool)
* Adobe Commerce: [Actualizar la herramienta de compatibilidad](https://devdocs.magento.com/upgrade-compatibility-tool/introduction.html) en nuestra documentación para desarrolladores.
