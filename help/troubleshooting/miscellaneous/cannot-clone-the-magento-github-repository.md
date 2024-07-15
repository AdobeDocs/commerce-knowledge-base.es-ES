---
title: No se puede clonar el repositorio de GitHub del Magento
description: Este artículo proporciona una corrección para los casos en los que no se puede clonar el repositorio de GitHub de Magento.
exl-id: 65de77b5-496d-42a3-ab2e-1fff9df97160
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---

# No se puede clonar el repositorio de GitHub del Magento

Este artículo proporciona una corrección para los casos en los que no se puede clonar el repositorio de GitHub de Magento.

## Detalle {#detail}

El error es similar al siguiente:

```terminal
Cloning into 'magento2'...
Permission denied (publickey).
fatal: The remote end hung up unexpectedly
```

## Solución {#solution}

Cargue su clave SSH en GitHub tal como se describe en [la página de ayuda de GitHub](https://help.github.com/articles/generating-ssh-keys) .
