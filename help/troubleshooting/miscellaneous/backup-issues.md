---
title: Problemas de copia de seguridad
description: Este artículo enumera las posibles soluciones para los problemas de creación de copias de seguridad.
exl-id: 1a6204ad-bd5a-46dc-8a8e-39655a174e09
feature: Storage, Data Import/Export
role: Developer
source-git-commit: 35d4f2130d0ec71f71f5f20aa8a7c76207e7a35a
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Problemas de copia de seguridad

Este artículo enumera las posibles soluciones para los problemas de creación de copias de seguridad.

## Productos y versiones afectados

* Adobe Commerce local 2.3.x
* Magento Open Source 2.3.x

## Copia de seguridad desactivada {#backup-disabled}

Si la funcionalidad de copia de seguridad de Adobe Commerce no se inicia o muestra el siguiente mensaje, debe habilitar la función antes de realizar la copia de seguridad.

```bash
Backup functionality is disabled.
Backup functionality is currently disabled. Please use other means for backups.
```

Introduzca el siguiente comando CLI:

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

Para obtener información adicional sobre las copias de seguridad, vea [Realizar copias de seguridad y revertir el sistema de archivos, los medios y la base de datos.](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-backup.html)

## Espacio en disco insuficiente {#insufficient-disk-space-trouble-backup-space-}

Si la copia de seguridad ha fallado debido a que no hay suficiente espacio en disco, normalmente debería liberar espacio en disco moviendo algunos archivos a otro dispositivo de almacenamiento o unidad. Sin embargo, puede haber otras formas de resolver el problema. Consulte uno de los siguientes recursos para obtener sugerencias:

* [8 consejos para resolver problemas de disco duro de sistemas Linux y Unix como Disco lleno o No se puede escribir en el disco](https://www.cyberciti.biz/datacenter/linux-unix-bsd-osx-cannot-write-to-hard-disk)
* [error del servidor: df indica que el disco está lleno, pero no lo está](https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not)
* [unix.stackexchange.com: ¿Rastreando dónde ha ido el espacio en disco en Linux?](https://unix.stackexchange.com/questions/125429/tracking-down-where-disk-space-has-gone-on-linux)

## Error del sistema operativo {#operating-system-error-trouble-backup-os-}

Desafortunadamente, no podemos recomendar nada específico debido a la variedad de errores que puede encontrar. Sin embargo, podemos sugerirle lo siguiente:

* Póngase en contacto con el administrador del sistema.
* Busque foros públicos como [Stack Exchange](https://unix.stackexchange.com) o [Stack Overflow](https://stackoverflow.com)
* Abra un [problema de GitHub](https://github.com/magento/magento2/issues) e intentaremos ayudarle.

## Error de copia de seguridad {#backup-fails-trouble-backup-all-}

Si la copia de seguridad falla o si todas las pruebas de copia de seguridad fallan, es posible que el [propietario del sistema de archivos de Adobe Commerce](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/file-sys-perms-over.html) no tenga suficientes privilegios y propiedad del sistema de archivos de Adobe Commerce. Por ejemplo, otro usuario podría ser el propietario de los archivos o éstos podrían ser de sólo lectura.

Preste especial atención a los permisos del sistema de archivos y a la propiedad del directorio y los subdirectorios `<magento_root>/var`. Para obtener más información, vea [Establecer permisos y propiedad del sistema de archivos](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-system-perms.html).
