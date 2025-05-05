---
title: Preguntas frecuentes sobre el informe Adobe Commerce [!DNL Site-Wide Analysis Tool]
description: Obtenga información acerca de [!DNL Site-Wide Analysis Tool], una herramienta de autoservicio proactiva y un repositorio central que incluye información detallada del sistema y recomendaciones para garantizar la seguridad y la operabilidad de la instalación de Adobe Commerce.
exl-id: 7c843d55-9e2c-4b18-8859-0ebad0ae28cf
feature: Best Practices, Saas, Support, Tools and External Services
role: Admin
source-git-commit: 580ad148cd4346868cd9892a1ae9a4d85f73edce
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Preguntas frecuentes sobre el informe Adobe Commerce [!DNL Site-Wide Analysis Tool]

>[!IMPORTANT]
>
>A partir del 23 de abril de 2024, [!DNL Site-Wide Analysis Tool] se retirará del mercado para todos los clientes locales de Adobe Commerce.

Este artículo proporciona una descripción del informe [!DNL Site-Wide Analysis Tool], generado automáticamente para los clientes de Adobe Commerce en la infraestructura en la nube con periodicidad mensual o trimestral.

>[!NOTE]
>
>En Adobe Commerce en la infraestructura en la nube v2.4.1 y superior, [!DNL Site-Wide Analysis Tool] está disponible a través del Panel de administración de Commerce. Por lo tanto, los informes de [!DNL Site-Wide Analysis Tool] los puede ejecutar directamente el cliente. Para obtener información de acceso, consulte la [[!DNL Site-Wide Analysis Tool] guía](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/access.html?lang=es).

## ¿Qué es [!DNL Site-Wide Analysis Tool]?

[!DNL Site-Wide Analysis Tool] es una aplicación SaaS que realiza análisis de sitio de clientes &quot;punto en tiempo&quot; de extremo a extremo (dentro del entorno [!DNL Site-Wide Analysis Tool], no en el sitio del cliente). Toda la información del sitio del cliente relacionada con [!DNL Site-Wide Analysis Tool] se recopila en horarios predeterminados de cada 3 horas a una vez al día. Esto significa que [!DNL Site-Wide Analysis Tool] está analizando constantemente los datos del sitio del cliente para buscar resultados.

## ¿Qué es un informe de [!DNL Site-Wide Analysis Tool]?

El informe [!DNL Site-Wide Analysis Tool] es una lista de resultados (problemas) con recomendaciones de prácticas recomendadas de autoservicio que se pueden enviar a los clientes en un formulario de PDF a través del sistema de tickets de asistencia de Adobe Commerce.

## ¿Qué información se incluye en un informe de [!DNL Site-Wide Analysis Tool]?

La información del sitio, proporcionada en el informe [!DNL Site-Wide Analysis Tool], incluye:

* búsqueda
   * Información general, incluida una &quot;Prioridad&quot; para el orden de las correcciones de implementación
   * Búsqueda de descripción
   * Condición(s) previa(s), si procede
   * Impacto(s) del sitio
   * Causa(s) principal(es)
   * Recomendación(es)
* Registros de excepciones
   * Registrar información de excepción
   * Fecha de la última incidencia
   * Número de veces que se produce la excepción

## ¿Quién recibe los informes mensuales automatizados [!DNL Site-Wide Analysis Tool]?

Actualmente, los clientes con un índice de estado de [!DNL Site-Wide Analysis Tool] bajo (que se encuentre en el umbral de rendimiento establecido actualmente o por debajo de este) recibirán un informe mensual de [!DNL Site-Wide Analysis Tool] para su entorno de producción mediante el sistema de tickets de asistencia.

## ¿Quién recibe los informes trimestrales automatizados [!DNL Site-Wide Analysis Tool]?

Todos los clientes, independientemente del índice de estado de [!DNL Site-Wide Analysis Tool], recibirán un informe trimestral de [!DNL Site-Wide Analysis Tool] para su entorno de producción a través del sistema de tickets de asistencia.

## ¿Cómo se entregan los informes?

[!DNL Site-Wide Analysis Tool] informes se entregan automáticamente a través del sistema de tickets de asistencia de Adobe Commerce mensualmente o trimestralmente. Los informes de [!DNL Site-Wide Analysis Tool] también se pueden generar manualmente desde el panel de [!DNL Site-Wide Analysis Tool] y guardarse en el escritorio. Estos [!DNL Site-Wide Analysis Tool] informes se pueden enviar por correo electrónico como datos adjuntos.

>[!NOTE]
>
>Después de aplicar una recomendación, la generación manual de un informe no actualiza las recomendaciones; es posible que pasen unos días antes de que se elimine de [!DNL Site-Wide Analysis Tool Dashboard].
