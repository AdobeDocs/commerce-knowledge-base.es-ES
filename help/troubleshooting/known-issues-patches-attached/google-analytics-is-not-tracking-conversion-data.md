---
title: Google Analytics no está realizando el seguimiento de los datos de conversión
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.2.4 relacionado con los Google Analytics que no realizan un seguimiento de los datos de conversión.
exl-id: b9012fd1-4f90-41e9-9559-0343ee052ec6
feature: Configuration, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Google Analytics no está realizando el seguimiento de los datos de conversión

Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.2.4 relacionado con los Google Analytics que no realizan un seguimiento de los datos de conversión.

>[!NOTE]
>
>El problema se solucionó en Adobe Commerce 2.2.6.

## Problema

Los Google Analytics no han realizado un seguimiento de los datos de conversión debido a un error en el código del componente Google Analytics.

<u>Pasos a seguir</u>:

1. Habilite y configure la funcionalidad de Google Analytics en el Administrador de Commerce en **Tiendas** > **Configuración** > **Configuración** > **Ventas** > **API de Google** > **Google Analytics**.
1. Clic **Guardar configuración**.
1. Realiza un pedido en la tienda.
1. Ir a **Panel de Google Analytics** > **Conversiones** > **Información general**.
1. Establezca el intervalo de fechas en la fecha actual.

<u>Resultado esperado</u>:

El orden aparece en los datos de conversión.

<u>Resultado real</u>:

El orden no aparece en los datos de conversión.

## Solución

El parche corrige el error en el código del componente Google Analytics. Después de aplicar el parche, los Google Analytics realizarán un seguimiento de los datos de conversión.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[Descargar MDVA-11263\_EE\_2.2.4\_v1.composer.patch](assets/MDVA-11263_EE_2.2.4_v1.composer.patch.zip)

### Versiones de Adobe Commerce compatibles:

El parche se ha creado para:

* Adobe Commerce local 2.2.4

El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce local 2.2.5
* Adobe Commerce en infraestructura en la nube 2.2.4, 2.2.5

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obtener instrucciones.

## Archivos adjuntos
