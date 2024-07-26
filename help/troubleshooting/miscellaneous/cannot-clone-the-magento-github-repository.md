---
title: No se puede clonar el repositorio de GitHub del Magento
description: Este artículo proporciona una corrección para los casos en los que no se puede clonar el repositorio de GitHub de Magento.
exl-id: 65de77b5-496d-42a3-ab2e-1fff9df97160
feature: Data Import/Export
role: Developer
source-git-commit: 35d4f2130d0ec71f71f5f20aa8a7c76207e7a35a
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---

# No se puede clonar el repositorio de GitHub del Magento

Este artículo proporciona una corrección para los casos en los que no se puede clonar el repositorio de GitHub de Magento.

## Detalle {#detail}

El error es similar al siguiente:

```bash
Cloning into 'magento2'...
Permission denied (publickey).
fatal: The remote end hung up unexpectedly
```

## Solución {#solution}

Cargue su clave SSH en GitHub tal como se describe en [la página de ayuda de GitHub](https://help.github.com/articles/generating-ssh-keys) .
