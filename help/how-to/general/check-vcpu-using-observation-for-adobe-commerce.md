---
title: Vea el nivel de vCPU del entorno en su clúster en Adobe Commerce
promoted: true
description: En este artículo se explica cómo comprobar la asignación del nivel de vCPU mediante la pestaña Información de New Relic en Observación para Adobe Commerce. Observación para Adobe Commerce es un nerdlet de New Relic que muestra el estado del sitio de Adobe Commerce, las vistas de tiempo actual y anterior.
exl-id: a0332e7e-d38d-47d3-b3da-293902f45edc
source-git-commit: 309fda5284de3b8be54e95bf2bfd8ff1777b6c90
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Vea el nivel de vCPU del entorno en su clúster en Adobe Commerce

En este artículo se explica cómo comprobar la asignación del nivel de vCPU mediante la pestaña Información de New Relic en Observación para Adobe Commerce. Observación para Adobe Commerce es un nerdlet de New Relic que muestra el estado del sitio de Adobe Commerce, las vistas de tiempo actual y anterior.

## Productos y versiones afectados:

Adobe Commerce en infraestructura en la nube 2.4.3 - 2.4.6

## Compruebe la asignación del nivel de vCPU con Observación para Adobe Commerce:

Para acceder e iniciar sesión en el nerdlet de New Relic Observation for Adobe Commerce:

1. En la página de inicio de New Relic, haga clic en **Aplicaciones**.
1. Haga clic en **Observación para Adobe Commerce**.
1. Se abre el nerdlet Observation for Adobe Commerce.
1. Haz clic en el menú desplegable **Seleccionar una cuenta** y selecciona una cuenta.
1. Puede rellenar el ID del proyecto, el número de cuenta de New Relic o el nombre de la cuenta, o examinar la lista de cuentas.
1. Haga clic en el menú desplegable azul claro con el icono del reloj (hacia la parte superior derecha de la ventana de nerdlet).
1. Si está intentando identificar la causa de un evento/problema, seleccione una hora antes de la fecha y hora del ticket para ver si hubo algún evento/dato anterior. Puede usar los lapsos de tiempo preestablecidos o establecer un lapso de tiempo personalizado seleccionando **Establecer personalizado**.
1. En las fichas, haga clic en **Información**. Hay tres gráficos de niveles de vCPU:
   * El primer gráfico muestra **vista de nivel de vCPU en la escala de tiempo MÁS DE 2 semanas (necesitará seleccionar una escala de tiempo MÁS DE 2 semanas). NOTA: La tasa de muestra será por día. Si los tamaños o las reducciones de tamaño del clúster se producen en un día, el tamaño del nivel final se mostrará al día siguiente**.
   * El segundo gráfico muestra **la vista del nivel de vCPU en la escala de tiempo (es necesario seleccionar una escala de tiempo SUPERIOR a 24 horas pero no superior a 2 semanas)**.
   * El tercer gráfico muestra la vista de nivel de **vCPU en la escala de tiempo POR NODO; debería ver la escala de tiempo MENOS de 24 horas**.

## Lectura relacionada

* [Resumen de la observación de Adobe Commerce](/help/support-tools/observation-for-adobe-commerce/observation-adobe-commerce-overview.md) en nuestra base de conocimiento de soporte.
