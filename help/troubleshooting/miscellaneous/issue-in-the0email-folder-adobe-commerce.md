---
title: Problema de permiso de carpeta var/export en Adobe Commerce en la nube
description: Este artículo proporciona una solución a un problema en el que no puede exportar datos de productos debido a un problema de permisos de archivo en el servidor en la carpeta var/export/email. Los síntomas incluyen exportaciones de productos y catálogos no disponibles en la interfaz de usuario, pero visibles al utilizar SSH.
exl-id: 68120d3b-f5df-43a5-91f6-2ec519cc25ac
feature: Cloud, Communications, Data Import/Export, Paas, Roles/Permissions
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Problema de permiso de carpeta var/export en Adobe Commerce en la nube

Este artículo proporciona una solución a un problema en el que no puede exportar datos de productos debido a un problema de permisos de archivos en el servidor de `var/export/email` carpeta. Los síntomas incluyen exportaciones de productos y catálogos no disponibles en la interfaz de usuario, pero visibles al utilizar SSH.

## Productos y versiones afectados

Adobe Commerce en infraestructura en la nube, 2.3.0-2.3.7-p2, 2.4.0-2.4.3-p1

## Problema

No puede exportar archivos en `var/export/email` o `var/export/archive` carpeta.
Esto no se pudo implementar debido a los permisos de `var/export/email` o `var/export/email/archive` porque esa carpeta de archivos se crea en forma de correo electrónico (y si solo realizo la exportación/correo electrónico a veces, sigue habiendo un problema) aparte de agregar algo para tener en cuenta la subcarpeta `var/export/email/archive`.

<u>Pasos a seguir</u>:

En el Administrador, vaya a **Sistema** > *Transferencia de datos* > **Exportar**.
Seleccione los archivos CSV que desea guardar en `var/export/` carpeta.

<u>Resultado esperado</u>:

Los archivos CSV son visibles y se pueden exportar.

<u>Resultado real</u>:

Los archivos CSV no son visibles. También verá un mensaje de permiso denegado: *RecursiveDirectoryIterator::__builds(/app/project id>/var/export/email): error al abrir dir: Permiso denegado*

Recibirá el mismo mensaje para todos los tipos de exportación: Advanced Pricing, Customer Finances, Customer Main File y Customer Addresses.

## Causa

Esto se debe a una carpeta creada dentro de `/var` que tiene permisos imperfectos: `d-wxrwsr-T`. El bit T sticky significa que los usuarios solo pueden eliminar los archivos que poseen, pero el ejecutable que falta significa que no pueden crear archivos en el directorio.

Esto suele notarse cuando el sistema crea una carpeta llamada `export`, que contiene una carpeta llamada `email`, que contiene una carpeta llamada `archive`.

Para comprobar si el directorio tiene estos permisos mal configurados, ejecute el siguiente comando en CLI/Terminal:

`ls -ld var/export/`

El resultado si los permisos están mal configurados es:

`d-wxrwsr-T 3 web web 4096 Aug 15 19:12 var/export/`


## Solución

Para solucionarlo, actualice los permisos de las carpetas a 777 y, a continuación, todos los archivos de forma recursiva, ejecutando los siguientes comandos:

```bash
chmod 777 var/export/
chmod 777 var/export/email/
chmod 777 var/export/email/archive/
chmod 777 -R var/export/
```

## Lectura relacionada

* [Exportar](https://docs.magento.com/user-guide/system/data-export.html) en nuestra guía del usuario.
