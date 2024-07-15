---
title: Error de falta de memoria durante la instalación o actualización
description: Este artículo habla sobre las soluciones para el error de falta de memoria durante la instalación/actualización de productos locales y locales de Magento Open Source de Adobe Commerce.
exl-id: c0ed8228-9357-4a3b-a102-1119386ea52a
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Error de falta de memoria durante la instalación o actualización

Este artículo habla sobre las soluciones para el error de falta de memoria durante la instalación/actualización de productos locales y locales de Magento Open Source de Adobe Commerce.

## Productos y versiones afectados

* Adobe Commerce local 2.3.x
* Magento Open Source local 2.3.x

## Problema

Al instalar o actualizar la aplicación o componentes de Adobe Commerce o Magento Open Source, como extensiones, temáticas o paquetes de idiomas, mediante el Asistente para instalación web, aparece un error similar al siguiente:

```bash
Could not complete update {"components":[
{"name":"magento/module-bundle-sample-data","version":"100.1.0"}
]} successfully: proc_open(): fork failed - Cannot allocate memory
```

El error

```bash
proc_open(): fork failed - Cannot allocate memory
```

también puede mostrarse en la línea de comandos.

## Solución {#solution}

Le recomendamos que [asigne 2 GB de memoria a PHP](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html) en nuestra documentación para desarrolladores para garantizar que la instalación o actualización se realice correctamente.

Si ya lo ha hecho, cree un archivo de intercambio en su equipo. Un equipo Linux usa *espacio de intercambio* si necesita más recursos de memoria y la RAM está llena. El espacio de intercambio se utiliza para páginas inactivas en la memoria.

Las siguientes son solo sugerencias; otras opciones podrían estar disponibles. Consulte con un administrador de red u otro recurso con conocimientos antes de continuar. Debe ejecutar los comandos para crear un archivo de intercambio como usuario con privilegios de `root`.

### Intercambiar archivo en Ubuntu {#swap-file-on-ubuntu}

Utilice el comando `fallocate` como se describe en estas referencias:

* [Cómo agregar un intercambio en Ubuntu 14.04 (Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04)
* [Cómo agregar espacio de intercambio en Ubuntu 16.04 (Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04)
* [Preguntas frecuentes sobre SwapFaq (help.ubuntu.com)](https://help.ubuntu.com/community/SwapFaq)

### Intercambiar archivo en CentOS {#swap-file-on-centos}

Utilice el comando `mkswap` como se describe en estas referencias:

* [Cómo agregar un intercambio en CentOS 6 (Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-6)
* [Cómo agregar un intercambio en CentOS 7 (Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-7)
* [Espacio de intercambio (portal para clientes de RedHat)](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/ch-swapspace.html)
