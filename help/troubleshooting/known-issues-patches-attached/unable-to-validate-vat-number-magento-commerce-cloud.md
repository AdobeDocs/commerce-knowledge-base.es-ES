---
title: 'No se puede validar el número de IVA: Adobe Commerce en la infraestructura en la nube'
description: Este artículo proporciona un parche para el problema en el que haya un error durante la verificación del número de IVA.
exl-id: 9868e888-bad8-4823-acab-4b3804933cb0
feature: Cloud, Customer Service, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# No se puede validar el número de IVA: Adobe Commerce en la infraestructura en la nube

Este artículo proporciona un parche para el problema en el que haya un error durante la verificación del número de IVA.

## Productos y versiones afectados

Todas las versiones de Adobe Commerce on-premise y Adobe Commerce en la nube hasta la 2.3.6 (incluida la 2.3.5-p1) se vieron afectadas, incluidas las versiones p1 y p2 ya publicadas. Esto incluye:

* 2,3,5-p1
* 2.3.5
* 2.3.4 - 2.3.4-p2
* 2.3.3 - 2.3.3-p1
* 2.3.2 -2.3.2-p2
* 2.0.0: 2.3.1

## Problema

<u>Pasos a seguir:</u>

1. Vaya a **Tiendas** > **Configuración** > **Clientes** > **Configuración del cliente** > **Crear nuevas opciones de cuenta** y establezca **Habilitar asignación automática** a **Grupo de clientes** en *Sí*.
1. Vaya a **General** > **Información de la tienda** > y establezca un país y un número de IVA válidos.
1. Haz clic en **Validar número de IVA**.

<u>Resultado esperado:</u>

La validación es correcta.

<u>Resultado real:</u>

Se muestra el siguiente error: &quot;*Error durante la verificación del número de IVA.*&quot;

## Solución

Aplique el [parche](assets/MDVA-27623_EE_2.3.2-p2_COMPOSER_v1.patch.zip) proporcionado en este artículo.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[MDVA-27623\_EE\_2.3.2-p2\_COMPOSER\_v1.patch](assets/MDVA-27623_EE_2.3.2-p2_COMPOSER_v1.patch.zip)

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obtener instrucciones.

## Archivos adjuntos
