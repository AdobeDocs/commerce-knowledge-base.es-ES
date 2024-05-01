---
title: Durante la instalación, advertencia de fecha PHP
description: Este artículo proporciona una corrección para una advertencia de fecha PHP durante la instalación.
exl-id: f82c77a9-bbcd-4426-96a0-b3f4b704860b
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '61'
ht-degree: 0%

---

# Durante la instalación, advertencia de fecha PHP

Este artículo proporciona una corrección para una advertencia de fecha PHP durante la instalación.

## Detalles {#details}

Durante la instalación, aparece el siguiente mensaje:

```text
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more]
```

### Solución {#solution}

Compruebe cuidadosamente la configuración de la zona horaria de PHP. Consulte [Guía de instalación > Configuración de PHP](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html) en nuestra documentación para desarrolladores.
