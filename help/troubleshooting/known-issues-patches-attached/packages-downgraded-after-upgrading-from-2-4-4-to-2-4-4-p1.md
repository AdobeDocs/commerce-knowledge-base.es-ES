---
title: Paquetes degradados después de actualizar de 2.4.4 a 2.4.4-p1
description: Este artículo proporciona una revisión para el problema que se produce cuando los comerciantes de la versión 2.4.4 ejecutan el comando "actualización del compositor" y, a continuación, los paquetes (módulos) que se enumeran a continuación se degradan a versiones anteriores que no son compatibles con la versión 2.4.4 y solo se supone que deben utilizarse con la versión 2.4.5 y superior.
exl-id: 4ebdbcd7-6905-4647-b071-1e4413455f38
feature: Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 0%

---

# Paquetes degradados después de actualizar de 2.4.4 a 2.4.4-p1

Este artículo proporciona una revisión para el problema que se produce cuando los comerciantes de la versión 2.4.4 ejecutan el comando `composer update` y, a continuación, los paquetes (módulos) que se enumeran a continuación se degradan a versiones anteriores que no son compatibles con la versión 2.4.4 y que solo se supone que deben usarse con la versión 2.4.5 y superior.

## Productos y versiones afectados

* Adobe Commerce en infraestructura en la nube 2.4.4
* Adobe Commerce local 2.4.4
* Magento Open Source 2.4.4

## Problema

Existen dos situaciones en las que puede producirse este problema y cómo puede reproducirse:

### Escenario 1

<u>Pasos a seguir</u>:

Al actualizar de 2.4.4 a 2.4.4-p1, hay una serie de paquetes (módulos) que se degradan con resultados similares:

```text
Downgrading magento/module-adobe-ims (2.1.4 => 2.1.3)
Downgrading magento/module-adobe-ims-api (2.1.2 => 2.1.1)
Downgrading magento/module-adobe-stock-admin-ui (1.3.2 => 1.3.1)
Downgrading magento/module-adobe-stock-client-api (2.1.2 => 2.1.1)
Downgrading magento/module-adobe-stock-image (1.3.3 => 1.3.2)
Downgrading magento/module-adobe-stock-image-admin-ui (1.3.3 => 1.3.2)
Downgrading magento/module-banner-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-inventory (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-advanced-checkout (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-api (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-bundle-product (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-catalog-api (1.3.3 => 1.3.2)
Downgrading magento/module-inventory-configurable-product-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-configurable-product-frontend-ui (1.0.3 => 1.0.2)
Downgrading magento/module-inventory-import-export (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-in-store-pickup-admin-ui (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-in-store-pickup-frontend (1.1.3 => 1.1.2)
Downgrading magento/module-inventory-in-store-pickup-graph-ql (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-in-store-pickup-sales-admin-ui (1.1.3 => 1.1.2-p1)
Downgrading magento/module-inventory-in-store-pickup-shipping (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-low-quantity-notification (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-low-quantity-notification-api (1.2.2 => 1.2.1-p1)
Downgrading magento/module-inventory-requisition-list (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-sales-admin-ui (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-sales-api (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-shipping-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-source-selection-api (1.4.2 => 1.4.1-p1)
Downgrading magento/module-inventory-wishlist (1.0.2 => 1.0.1)
Downgrading magento/module-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-re-captcha-checkout-sales-rule (1.1.1 => 1.1.0)
Downgrading magento/module-re-captcha-customer (1.1.3 => 1.1.2)
Downgrading magento/module-re-captcha-frontend-ui (1.1.3 => 1.1.2)
Downgrading magento/module-staging-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-two-factor-auth (1.1.4 => 1.1.3)
Removing magento/module-admin-adobe-ims (100.4.0)
```

<u>Resultados esperados</u>:

La actualización de la versión 2.4.4 a 2.4.4-p1 da como resultado los paquetes (módulos) correctos para la versión 2.4.4-p1.

<u>Resultados reales</u>:

Durante la actualización de la versión 2.4.4 a la 2.4.4-p1, las versiones de estos paquetes (módulos) se degradan, pero estos mensajes se pueden ignorar y la funcionalidad no se ve afectada.

### Escenario 2

<u>Pasos a seguir</u>:

Cuando los comerciantes de 2.4.4 ejecutan el comando `composer update`, los mismos paquetes (módulos) enumerados arriba en el escenario **1** se actualizan a sus versiones más recientes que solo son compatibles con la versión 2.4.5 y no se supone que se deben usar con la versión 2.4.4.

<u>Resultados esperados</u>:

La actualización de la versión 2.4.4 a 2.4.4-p1 da como resultado los paquetes (módulos) correctos para la versión 2.4.4-p1.

<u>Resultados reales</u>:

Los paquetes (módulos) se descargan después de actualizar de la versión 2.4.4 a la 2.4.4-p1.

## Solución 1: parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre de archivo o en el vínculo siguiente: [Descargar ACPLTSRV-2017-fix.sh.zip](assets/ACPLTSRV-2017-fix.sh.zip)

## Versiones compatibles de Adobe Commerce y Magento Open Source:

El parche se ha creado para:

* Adobe Commerce en infraestructura en la nube 2.4.4
* Adobe Commerce local 2.4.4
* Magento Open Source 2.4.4

>[!NOTE]
>
>El parche no es compatible con ninguna otra versión ni edición de Adobe Commerce ni de Magento Open Source.

## Cómo aplicar el parche

Use el script bash adjunto [ACPLTSRV-2017-fix.sh.zip](assets/ACPLTSRV-2017-fix.sh.zip) como solución alternativa a este problema.

**Instrucciones exactas sobre cómo usar el script:**

### En Adobe Commerce sobre la infraestructura en la nube:

1. Descargue el archivo de script bash `ACPLTSRV-2017-fix.sh` en su registro local de la base de código de la nube.
1. Ejecute el archivo de script bash `ACPLTSRV-2017-fix.sh` para modificar los archivos del compositor localmente.
1. Añada y confirme los archivos del compositor modificado en su repositorio de Git.

### En Adobe Commerce o Magento Open Source local:

1. Coloque el script bash `ACPLTSRV-2017-fix.sh` en la carpeta `root` de su instalación de Adobe Commerce/Magento Open Source 2.4.4 (la misma carpeta que `composer.json`).
1. Ejecute el script bash con un argumento `apply` para bloquear los paquetes afectados (módulos) a sus versiones 2.4.4:

   ```bash
   sh ACPLTSRV-2017-fix.sh apply
   ```

1. Ejecutar Compositor actualizado para instalar los paquetes bloqueados (módulos).
1. Una vez que esté listo para actualizar a 2.4.5 o 2.4.4-p1, ejecute el script con un argumento `rollback`:

   ```bash
   sh ACPLTSRV-2017-fix.sh rollback
   ```

   Si se omite este paso, se producirán errores de actualización debido a requisitos de paquetes (módulos) en conflicto.
1. Una vez completados los pasos anteriores, puede comenzar la actualización.

## Solución 2

La segunda solución para este problema es no ejecutar el comando `composer update` sin ningún argumento.
