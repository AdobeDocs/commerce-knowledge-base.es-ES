---
title: Diagnóstico de una discrepancia de datos
description: Este artículo proporciona soluciones para la resolución de discrepancias entre un informe de Magento Business Intelligence (MBI) y una consulta o un informe de terceros.
exl-id: 7d1156cb-9e9b-4426-a0ca-8890b815c245
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Diagnóstico de una discrepancia de datos

Este artículo proporciona soluciones para la resolución de discrepancias entre un informe de Magento Business Intelligence (MBI) y una consulta o un informe de terceros.

Según la complejidad del análisis, la generación del informe de MBI correspondiente puede requerir estar familiarizado con una serie de facetas diferentes de la plataforma. Esta lista de comprobación y los vínculos relacionados le ayudarán a comprender la lógica subyacente al informe, lo que le permitirá identificar el origen de cualquier discrepancia.

1. Si otro miembro de su equipo creó el informe, comience por confirmar el objetivo y los parámetros de su análisis.
1. Genere los puntos de datos esperados para compararlos con el informe de MBI en función de una consulta, una herramienta de informes de terceros o una fórmula.
1. Revise y confirme la [métrica](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-metrics.html) definiciones, ya sea desde el vínculo de métrica en Report Builder o visitando la [Resumen del sistema](https://support.magento.com/hc/en-us/articles/360016730971-Understand-View-definitions-of-metrics-filters-columns-and-column-references-in-the-System-Summary) pestaña:
   * Tabla de datos
   * Operación
   * Columna de operador, incluido su cálculo si se deriva (a través de Resumen del sistema)
   * Marca de tiempo
   * Para métricas de suscripción: fechas de inicio y finalización
   * Filtros, incluidos los contenidos en cualquier [conjuntos de filtros](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-filters.html) aplicado
1. Revise y confirme cualquier otra manipulación de datos dentro del informe:
   * Fórmulas calculadas
   * [Agrupaciones](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html#groupby)
   * [Perspectivas](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html)
   * [Opciones de tiempo](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html)
   * Para [análisis de cohorte](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): Fecha de cohorte
   * Para [análisis de cohorte](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): Perspectiva de cohorte
1. Si la discrepancia implica datos recientes, confirme el punto de datos disponible más reciente consultando la **Actualizar detalles** de la página Conexiones.
1. Si una métrica utilizada en el análisis se crea en una tabla de la base de datos donde alguna vez se eliminan filas de esa tabla, confirme con el equipo de soporte de MBI que se está comprobando si la tabla contiene filas eliminadas, así como la frecuencia de la nueva comprobación y la [método de replicación](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html) para la tabla.
1. Del mismo modo, si las columnas utilizadas en el análisis se pueden modificar después de añadir una fila, confirme con la ayuda de que estas columnas se están [comprobado para modificaciones](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html), así como la frecuencia de la nueva comprobación.

**¿Todavía está trastornado?** No te preocupes, estamos aquí para ayudar. Envíenos una solicitud utilizando [estas instrucciones](/help/troubleshooting/miscellaneous/mbi-data-discrepancies.md).
