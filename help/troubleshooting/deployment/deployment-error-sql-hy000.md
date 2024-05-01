---
title: "Error de implementación: SQLSTATE[HY000]"
description: Este artículo proporciona una solución para el problema en el que la implementación falla debido al error SQLSTATE[HY000].
exl-id: c6da6275-9327-4a5c-99ed-93a53952ba42
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---

# Error de implementación: SQLSTATE[HY000]

Este artículo proporciona una solución para el problema en el que la implementación falla debido a SQLSTATE[HY000] error.

## Productos y versiones afectados

* Adobe Commerce, [todos los métodos de implementación](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Se produce un error SQLSTATE durante la implementación.

```sql
Updating modules:
SQLSTATE[HY000]: General error: 23 Out of resources when opening file '/tmp/#sql_565c_0.MAD' (Errcode: 24 "Too many open files"),
```

## Causa

Cron se ejecuta durante la implementación.

## Solución

Para resolver el problema, detenga la ejecución de cron abriendo la línea de comandos y ejecutando el siguiente comando:
`./vendor/bin/ece-tools cron:disable`.
