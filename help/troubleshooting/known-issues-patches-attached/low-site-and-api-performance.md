---
title: Bajo rendimiento del sitio y la API
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce en la infraestructura en la nube 2.2.1 relacionado con un bajo rendimiento del sitio y la API provocado por un largo tiempo necesario para escribir debug.log.
exl-id: b71816cd-f580-4c80-9694-585ed051a56d
feature: REST, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Bajo rendimiento del sitio y la API

Este artículo proporciona un parche para el problema conocido de Adobe Commerce en la infraestructura en la nube 2.2.1 relacionado con un bajo rendimiento del sitio y la API debido a un tiempo prolongado necesario para escribir `debug.log`.

## Problema

El rendimiento del sitio es lento. Las operaciones de API se ejecutan lentamente; por ejemplo, actualizando productos mediante el método `PUT`. Si examina más de cerca las operaciones con New Relic, la mayor parte de la memoria y la CPU se consumen escribiendo en `/var/log/debug.log`.

## Solución

Para resolver el problema, aplique el parche. El parche divide y escribe los registros de registro, pago y métodos de envío en archivos independientes.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[Descargar MDVA-8371\_EE\_2.2.1\_COMPOSER\_v2.patch](assets/MDVA-8371_EE_2.2.1_COMPOSER_v2.patch.zip)

### Versiones de Adobe Commerce compatibles

El parche se ha creado para:

* Adobe Commerce en la infraestructura en la nube 2.2.1

El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe:

* Adobe Commerce en la infraestructura en la nube 2.2.0, 2.2.2, 2.2.3
* Adobe Commerce local 2.2.0, 2.2.2, 2.2.3

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de asistencia para obtener instrucciones.

## Archivos adjuntos
