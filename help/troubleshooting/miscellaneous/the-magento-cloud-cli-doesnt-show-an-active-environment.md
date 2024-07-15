---
title: La nube de Magento  [!DNL CLI]  no muestra un entorno activo
description: En este artículo se describe un problema conocido de Adobe Commerce en el cual Magento-cloud [!DNL CLI]  (herramienta de línea de comandos) no muestra un entorno activo.
feature: Cloud, Integration, Configuration
role: Developer
exl-id: 3c1b5de2-8888-4531-9dc1-cd478e3c96fc
source-git-commit: 5eac8bb54e205eff6a96e279295cd12db1009f0a
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 0%

---

# `Magento-cloud` [!DNL CLI] no muestra un entorno activo

## Problema

Hay varios entornos activos y está intentando interactuar con un entorno ejecutando un comando `Magento-cloud` [!DNL CLI] (herramienta de línea de comandos). (Por ejemplo: `ssh`, `db:size`, `db:sql`, etc.)
Sin embargo, el indicador para elegir el entorno deseado no muestra este entorno. (Por ejemplo: el entorno de integración)

```
Enter a number to choose an environment:
Default: master
  [0] integration2 (type: development)
  [1] master (type: development)
  [2] production
  [3] staging
 >
```

## Causa

Es posible que el entorno no esté disponible debido a una implementación en curso, atascada o fallida.

## Solución

Deberá especificar manualmente el entorno con el indicador `e|-environment`.

1. Busque la lista de entornos activos y tome nota de los nombres de los entornos:

```
$ magento-cloud environment: list |grep "Active\|ID"
Your environments are:

| ID                     | Title            | Status       | Type           |
| Master                 | Master           | Active       | Development    |
|   Production           | Production       | Active       | Production     |
|     Staging            | Staging          | Active       | Staging        |
|       Integration      | Integration      | Active       | Development    |
|          Integration 2 | Integration 2    | Active       | Development    |
```

2. Especifique el ID del entorno con el comando:

`magento-cloud ssh -e integration`
