---
title: La consulta de GraphQL para ocultar categorías no funciona con el catálogo compartido B2B
description: Este artículo proporciona una solución para los casos en los que la función de catálogo compartido B2B no funciona con la consulta de categorías de GraphQL para ocultar categorías.
exl-id: bdafa8d9-b637-409e-86b5-d132bccfe0b8
feature: B2B, Catalog Management, Categories, GraphQL, Customer Service
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# La consulta de GraphQL para ocultar categorías no funciona con el catálogo compartido B2B


## Productos y versiones afectados

* Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.4.3

## Problema

Las categorías de GraphQL y las consultas `categoryList` omiten el permiso de categoría para ocultar categorías en un catálogo compartido. Esto les sucede a todos los comerciantes en Adobe Commerce 2.4.3 con la función de catálogo compartido B2B activada.

<u>Pasos a seguir</u>:

Requisitos previos:

Esto les sucede a todos los comerciantes en Adobe Commerce 2.4.3 con una tienda de PWA que consume la API de GraphQL con un backend/administrador de Adobe Commerce que tiene la función de catálogo compartido B2B activada.

1. Cree varias categorías (CAT1,CAT2).
1. Cree un catálogo compartido privado.
1. Cree un usuario de empresa y asígnelo al catálogo compartido anterior.
1. Asigne algunos productos a cada una de estas categorías.
1. Asigne CAT1 al catálogo personalizado y anule la asignación de CAT2 al catálogo privado personalizado. Esto anula la asignación de todos los productos CAT2 del catálogo compartido.
1. Guarde el catálogo personalizado.
1. Establezca el permiso de categoría para CAT2 en *Denegar* categoría de exploración y establezca el grupo de clientes en el catálogo privado anterior.
1. Ejecute la consulta `categoryList query` o las categorías como usuario de la compañía desde el paso tres.

<u>Resultados esperados</u>:

En los resultados solo aparece el CAT1.

<u>Resultados reales</u>:

Todas las categorías aparecen independientemente de si están asignadas o no en el catálogo compartido o de cuáles son los permisos de categoría.

## Causa

No se ha implementado la funcionalidad.

## Solución

El problema se solucionará en el ámbito de la versión 2.4.4, y los comerciantes deberían [enviar un ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para obtener un parche personalizado si necesitan una solución antes de la versión 2.4.4.

## Lectura relacionada

* [Límites en el número de categorías de Adobe Commerce de prácticas recomendadas](https://support.magento.com/hc/en-us/articles/360048176832) en nuestra base de conocimiento de soporte.
