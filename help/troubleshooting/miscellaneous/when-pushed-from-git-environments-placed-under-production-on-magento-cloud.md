---
title: Nuevos entornos colocados en producción cuando se insertan desde Git
description: Este artículo proporciona una solución para el problema en el que los nuevos entornos se colocan en el entorno de producción en Adobe Commerce en la infraestructura de la nube cuando se insertan desde el sistema de control de versiones de Git.
exl-id: 279cd6d8-fd45-45ba-8456-8b397a01976f
feature: Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '296'
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

Una rama principal solo se puede establecer después de que el comerciante haya insertado una rama recién creada y la haya activado. Consulte [Adobe Commerce en la infraestructura de la nube > Integración de Bitbucket](https://devdocs.magento.com/cloud/integrations/bitbucket-integration.html#create-a-new-cloud-branch) en nuestra documentación para desarrolladores.

Para actualizar un elemento principal para la rama existente en el servidor, utilice el comando `magento-cloud environment:info` en la CLI de Magento en la nube.

Ejemplo de uso:

`magento-cloud environment:info parent Staging`

Esto establecerá la rama principal en &quot;Ensayo&quot; para la rama extraída actualmente.

## Lectura relacionada

* [Adobe Commerce en la infraestructura de la nube > magento-cloud CLI](https://devdocs.magento.com/cloud/reference/cli-ref-topic.html) en nuestra documentación para desarrolladores.
