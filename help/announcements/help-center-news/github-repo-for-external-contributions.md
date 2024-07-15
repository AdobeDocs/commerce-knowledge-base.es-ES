---
title: La Base de conocimiento de asistencia de Adobe Commerce comienza a aceptar contribuciones
description: A partir del 15 de junio, el equipo de la Base de conocimiento de asistencia de Adobe Commerce comienza a aceptar ediciones directas y contribuciones de nuevos artículos de la comunidad externa de Adobe Commerce a través del repositorio de [magento/base de conocimiento](https://github.com/magento/knowledge-base) GitHub.
exl-id: b5198de0-d6b5-4107-8b74-a12606583596
feature: Support
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# La Base de conocimiento de asistencia de Adobe Commerce comienza a aceptar contribuciones

A partir del 15 de junio, el equipo de la Base de conocimiento de soporte de Adobe Commerce aceptará ediciones directas y contribuciones de nuevos artículos de la comunidad de Adobe Commerce externa a través del repositorio de [magento/base de conocimiento](https://github.com/magento/knowledge-base) GitHub.

¿Ha observado un error tipográfico en uno de nuestros artículos o pasos incompletos para la resolución de problemas?
Ahora puede solucionarlo usted mismo y obtener puntos de contribución.

## Contribute

Agradecemos todo tipo de contribuciones, desde correcciones menores de errores tipográficos hasta artículos completos de resolución de problemas. La contribución a este repositorio le permite obtener puntos de recompensa, de forma similar a la contribución al código Adobe Commerce y a la documentación para desarrolladores. Consulte [Puntos de recompensa por contribución](https://github.com/magento/knowledge-base/blob/main/docs/contribution-points.md) para obtener más información.

### Flujo de contribución general

1. Ramificar este repositorio.
1. Realice ediciones en el repositorio ramificado.
1. Enviar una solicitud de extracción (PR) a este repositorio.
1. Las pruebas se ejecutan:
   * CLA de Adobe: asegúrese de que se ha firmado el Contrato de licencia para colaboradores de Adobe Open Source.
   * Prueba de Markdown Linting: asegúrese de que la sintaxis de markdown sea correcta.
   * Prueba de validación de estructura de archivos: asegúrese de que la confirmación se realice de acuerdo con la [estructura de archivos requerida](https://github.com/magento/knowledge-base/blob/main/.github/CONTRIBUTING.md#file_structure).
1. Flujo de aprobaciones de PR:
   1. Los redactores de la base de conocimiento de soporte (KB) revisan las PR en un plazo de varios días y añaden etiquetas.
   1. El escritor de KB puede aprobar, denegar o solicitar cambios.
   1. Si se aprueba, el escritor de KB agrega etiquetas correspondientes al nivel de entrada proporcionado en PR y el experto en la materia interna (SME) revisa la PR.
   1. Los EM pueden aprobar, denegar o solicitar cambios.
1. Una vez realizadas todas las correcciones (si se solicita) y tanto el escritor de KB como el SME aprueban el PR, el escritor de KB importa contenido al repositorio interno y lo combina internamente.
1. El repositorio [magento/Knowledge-base](https://github.com/magento/knowledge-base) se sincroniza con el interno en 20 minutos.
1. Una vez sincronizados los repositorios, su PR se cerrará y obtendrá [puntos de contribución](#contribution-points).

Para obtener más información sobre el flujo de contribución, consulte la [Guía del colaborador](https://github.com/magento/knowledge-base/blob/main/.github/CONTRIBUTING.md).
Para plantillas, guías de estilo e instrucciones de formato, consulte [Documentación](https://github.com/magento/knowledge-base/tree/main/docs).

### Busque el archivo del artículo de la BC de asistencia en Github.

En la Base de conocimiento de soporte (KB), los artículos están organizados en secciones, que se anidan en categorías.

Por ejemplo, el artículo [Cómo suscribirse a las actualizaciones de estado del Magento de Adobe](/help/how-to/general/how-to-subscribe-to-adobe-magento-status-updates.md) pertenece a la sección General de la categoría Cómo.

Puede ver la sección y el nombre de la categoría en la ruta de rutas de exploración de la página del artículo; vea la siguiente imagen:

![rutas de exploración de categoría y sección](assets/breadcrumbs.png)

Los archivos de artículo se organizan del mismo modo en el repositorio [magento/base de conocimiento](https://github.com/magento/knowledge-base).
Todo el contenido se almacena en la carpeta `src`, con carpetas para categorías y carpetas anidadas para secciones; los nombres de archivo coinciden con los títulos de los artículos o son similares.

También puede utilizar la búsqueda dentro del repositorio utilizando un fragmento de texto del artículo de la BC de asistencia como cadena de búsqueda. Cuando la búsqueda devuelva archivos que contengan esta cadena, asegúrese de elegir el archivo que pertenezca a la sección y categoría correctas.

### Puntos de contribución

El repositorio [magento/base de conocimiento](https://github.com/magento/knowledge-base) está integrado con la comunidad de ingenieros de Magento para obtener puntos de contribución y soporte.

Consulte el documento [Puntos de contribución](https://github.com/magento/knowledge-base/blob/main/docs/contribution-points.md) para ver cómo se recompensan los puntos.
