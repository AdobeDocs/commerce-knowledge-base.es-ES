---
title: Falta el archivo de configuración o está alterado
description: Resuelva el problema con los archivos de configuración faltantes o alterados para Adobe Commerce.
exl-id: d80bf981-8ba6-4357-a841-57bf5d3f2a3f
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# Falta el archivo de configuración o está alterado

Este artículo explica cómo resolver el problema de si los archivos de configuración se han alterado o no están presentes.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, todas las versiones

## Problema

Los archivos de configuración `config.php` y/o `env.php` se cambiaron incorrectamente o faltan.

## Solución

El proceso de implementación crea un archivo de copia de seguridad para cada archivo de configuración:

* `app/etc/config.php.bak`: contiene la configuración específica del sistema y se genera automáticamente durante la compilación si no existe
* `app/etc/env.php.bak` — contiene datos de configuración confidenciales

Puede restaurarlos con el comando ECE-tools `backup:restore`.

Los archivos BAK son un producto del proceso de implementación. Si cambia manualmente un archivo de configuración después de la implementación, los cambios no se reflejarán en los archivos BACK existentes.

Para restaurar los archivos de configuración:

1. Inicie sesión en el repositorio remoto usando [SSH](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh).
1. Enumerar los archivos de copia de seguridad disponibles.

   ```
   ./vendor/bin/ece-tools backup:list
   ```

   ```
   The list of backup files:
   app/etc/env.php
   app/etc/config.php
   ```

1. Restaure los archivos de configuración.

   ```
   ./vendor/bin/ece-tools backup:restore
   ```

   Recibirá una lista de los archivos de configuración existentes afectados por la restauración.

   ```
   app/etc/env.php file exists! If you want to rewrite existed files use --force
   app/etc/config.php file exists! If you want to rewrite existed files use --force
   ```

1. Utilice la opción `--force` para sobrescribir todos los archivos.

   ```
   ./vendor/bin/ece-tools backup:restore --force
   ```

   ```
   Command backup:restore with option --force will rewrite your existed files. Do you want to continue [y/N]?y
   Backup file app/etc/env.php was restored.
   Backup file app/etc/config.php was restored.
   ```

1. Opcionalmente, puede restaurar un archivo de configuración específico.

   ```
   ./vendor/bin/ece-tools backup:restore --force --file=app/etc/config.php
   ```

   ```
   Command backup:restore with option --force will rewrite your existed files. Do you want to continue [y/N]?y
   Backup file app/etc/config.php was restored.
   ```
