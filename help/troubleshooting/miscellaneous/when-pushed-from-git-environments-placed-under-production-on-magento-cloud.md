---
title: Nuevos entornos colocados en producción cuando se insertan desde Git
description: Este artículo proporciona una solución para el problema en el que los nuevos entornos se colocan en el entorno de producción en Adobe Commerce en la infraestructura de la nube cuando se insertan desde el sistema de control de versiones de Git.
exl-id: 279cd6d8-fd45-45ba-8456-8b397a01976f
feature: Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%
---
# Nuevos entornos colocados en producción cuando se insertan desde Git

Este artículo proporciona una solución para el problema en el que los nuevos entornos se colocan en el entorno de producción en Adobe Commerce en la infraestructura de la nube cuando se insertan desde el sistema de control de versiones de Git.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, [todas las versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problema

<u>Requisitos previos</u>:

Tener un clon local controlado por Git del proyecto.

<u>Pasos a seguir</u>:

Debe crear una rama de integración desde la rama de ensayo:

1. Cambie a la rama de ensayo ejecutando el siguiente comando en el shell local: `git checkout staging`
1. Cree una rama de integración desde la rama de ensayo ejecutando el siguiente comando en el shell local: `git checkout -b <branch>`
1. Inserte la rama en el repositorio remoto y configure una rama ascendente ejecutando el siguiente comando en el shell local: `git push --set-upstream origin <branch>`

<u>Resultados esperados</u>:

La nueva rama se crea en la rama de ensayo.

<u>Resultados reales</u>:

La nueva rama se creó en la rama de producción.

## Causa

Esto no es un error. Para configurar una rama principal para otra rama, el comerciante debe utilizar la CLI de Magento en la nube.

## Solución

Una rama principal solo se puede establecer después de que el comerciante haya insertado una rama recién creada y la haya activado. Consulte [Adobe Commerce en la infraestructura de la nube > Integración de Bitbucket](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/integrations/bitbucket#create-a-cloud-branch) en nuestra documentación para desarrolladores.

Para actualizar un elemento principal para la rama existente en el servidor, utilice el comando `magento-cloud environment:info` en la CLI de Magento en la nube.

Ejemplo de uso:

`magento-cloud environment:info parent Staging`

Esto establecerá la rama principal en &quot;Ensayo&quot; para la rama extraída actualmente.

## Lectura relacionada

* [Adobe Commerce en la infraestructura de la nube > magento-cloud CLI](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-overview) en nuestra documentación para desarrolladores.
