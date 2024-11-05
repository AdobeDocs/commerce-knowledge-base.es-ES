---
title: Diagnóstico de una discrepancia de datos
description: Este artículo proporciona soluciones para la resolución de discrepancias entre un informe de Magento Business Intelligence (MBI) y una consulta o un informe de terceros.
exl-id: 7d1156cb-9e9b-4426-a0ca-8890b815c245
feature: Commerce Intelligence
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Diagnóstico de una discrepancia de datos

Este artículo proporciona soluciones para la resolución de discrepancias entre un informe de Magento Business Intelligence (MBI) y una consulta o un informe de terceros.

Según la complejidad del análisis, la generación del informe de MBI correspondiente puede requerir estar familiarizado con una serie de facetas diferentes de la plataforma. Esta lista de comprobación y los vínculos relacionados le ayudarán a comprender la lógica subyacente al informe, lo que le permitirá identificar el origen de cualquier discrepancia.

1. Si otro miembro de su equipo creó el informe, comience por confirmar el objetivo y los parámetros de su análisis.
1. Genere los puntos de datos esperados para compararlos con el informe de MBI en función de una consulta, una herramienta de informes de terceros o una fórmula.
1. Revise y confirme las definiciones de [metric](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-metrics.html), ya sea desde el vínculo de métrica en Report Builder o visitando la pestaña [Resumen del sistema](https://support.magento.com/hc/en-us/articles/360016730971-Understand-View-definitions-of-metrics-filters-columns-and-column-references-in-the-System-Summary):
   * Tabla de datos
   * Operación
   * Columna de operador, incluido su cálculo si se deriva (a través de Resumen del sistema)
   * Marca de tiempo
   * Para métricas de suscripción: fechas de inicio y finalización
   * Se han aplicado filtros, incluidos los contenidos en [conjuntos de filtros](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-filters.html)
1. Revise y confirme cualquier otra manipulación de datos dentro del informe:
   * Fórmulas calculadas
   * [Agrupaciones](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html#groupby)
   * [Perspectivas](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html)
   * [Opciones de tiempo](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html)
   * Para [análisis de cohorte](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): Fecha de cohorte
   * Para [análisis de cohorte](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): perspectiva de cohorte
1. Si la discrepancia se refiere a datos recientes, confirme el punto de datos disponible más reciente consultando la sección **Actualizar detalles** en la página Conexiones.
1. Si una métrica utilizada en el análisis se genera en una tabla de la base de datos donde alguna vez se eliminan filas de esa tabla, confirme con el equipo de soporte de MBI que se está comprobando si la tabla tiene filas eliminadas, así como la frecuencia de la nueva comprobación y el [método de replicación](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html) de la tabla.
1. Del mismo modo, si las columnas utilizadas en el análisis se pueden modificar después de agregar una fila, confirme con soporte técnico que estas columnas se están [comprobando si hay modificaciones](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html), así como la frecuencia de la nueva comprobación.

**¿Aún está trastornado?** No se preocupe: estamos aquí para ayudarle. Envíenos una solicitud utilizando [estas instrucciones](/help/troubleshooting/miscellaneous/mbi-data-discrepancies.md).

## Lectura relacionada

[Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce
