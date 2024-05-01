---
title: Cómo aplicar un parche del compositor proporcionado por el Adobe
description: Este artículo explica cómo aplicar un parche del compositor para Adobe Commerce local, Adobe Commerce en la infraestructura en la nube y Magento Open Source.
exl-id: a9301ad8-1d4b-49f5-b679-758624928219
feature: Cache
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Cómo aplicar un parche del compositor proporcionado por el Adobe

Este artículo explica cómo aplicar un parche del compositor para Adobe Commerce local, Adobe Commerce en la infraestructura en la nube y Magento Open Source.

>[!WARNING]
>
>Recomendamos encarecidamente aplicar y probar el parche en el entorno de ensayo/integración antes de aplicarlo a producción. También le recomendamos que tenga una copia de seguridad reciente antes de realizar cualquier manipulación.

## Cómo aplicar un parche del compositor para Adobe Commerce en la infraestructura en la nube {#cloud}

1. Si no tiene un directorio llamado `m2-hotfixes` en la raíz del proyecto, cree uno.
1. Copie el `%patch_name%.composer.patch` archivo(s) a `m2-hotfixes` directorio.
1. Añada, confirme e inserte los cambios de código:

   ```git
   git add -A
   ```

   ```git
   git commit -m "Apply %patch_name%.composer.patch patch"
   ```

   ```git
   git push origin
   ```

Para obtener información adicional sobre la aplicación de parches a proyectos en la nube, consulte [Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

### Cómo aplicar un parche del compositor para Adobe Commerce local y de Magento Open Source {#commerce}

1. Cargue el parche en el directorio raíz del Magento Open Source o local de Adobe Commerce.
1. Ejecute el siguiente comando SSH:

   ```bash
   patch -p1 < %patch_name%.composer.patch
   ```

   (Si el comando anterior no funciona, intente utilizar `-p2` en lugar de `-p1` )

1. Para que se reflejen los cambios, actualice la caché en el Administrador en **Sistema** > **Administración de caché**.
