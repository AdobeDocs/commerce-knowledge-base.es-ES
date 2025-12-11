---
title: Rendimiento lento debido a la reindexación completa
description: Este artículo proporciona una corrección para el bajo rendimiento debido a la reindexación completa (donde los datos de las tablas de base de datos relacionadas con la indexación se actualizan).
exl-id: 4f20a862-cf54-4196-8a88-101f0c80f8f1
feature: Best Practices
role: Developer
source-git-commit: 0786763a1db386fbea7f809eba9bc7f202cdd27a
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# Rendimiento lento debido a la reindexación completa

Este artículo proporciona una corrección para el bajo rendimiento debido a la reindexación completa (donde los datos de las tablas de base de datos relacionadas con la indexación se actualizan).

## Versiones y productos afectados

* Adobe Commerce en infraestructura en la nube 2.x.x
* Adobe Commerce local 2.x.x

### Problema

El vaciado constante y la reconstrucción de índices son algunas de las razones de la degradación del rendimiento. Además, la reindexación completa constante añade bloqueos en las tablas, lo que hace que el sitio web funcione mucho más lentamente de lo esperado.

### Causa

Se han realizado desde la administración acciones que pueden producir una reindexación completa, que incluyen:

* Guardado de atributo de producto
* Sitio web/tienda/tienda ver guardar
* Configuración de tienda

>[!NOTE]
>
>Estas acciones deben ejecutarse fuera del horario laboral para asegurarse de que no afecten al rendimiento durante el horario laboral.

[Las extensiones de terceros](https://support.magento.com/hc/en-us/articles/360042361152-Best-Practices-for-using-third-party-extensions-in-Magento) también pueden causar reindexación completa. El reindexado completo también se puede ejecutar manualmente desde CLI. Para saber si tiene índices que se están reindexando y que podrían causar una reducción del rendimiento:

1. Realice esta consulta para encontrar los indexadores que se han reindexado completamente en los últimos 15 minutos:

   ```
   SELECT * FROM indexer_state WHERE updated > NOW() - INTERVAL 15 MINUTE;
   ```

   Un nombre de indizador en la salida significa que el indizador se ha reindexado al menos una vez durante los últimos 15 minutos.

1. Si ha encontrado reindexación completa frecuente, investigue lo siguiente:
   * Quién podría estar haciendo esto manualmente desde la CLI
   * Qué módulo de terceros está haciendo la reindexación
   * Qué módulo de terceros marca indizadores como *No válido*

### Solución

Ejecute la reindexación solo cuando sea necesario. Para ver los pasos, revise [Configurar indizadores](https://experienceleague.adobe.com/es/docs/commerce-operations/configuration-guide/cli/manage-indexers#configure-indexers) en nuestra documentación para desarrolladores. Una recomendación general y una práctica recomendada es permitir que el mecanismo de reindexación parcial se ocupe de la reindexación de datos sin que un comerciante tenga que realizar ninguna acción manual. Toda reindexación debe realizarse utilizando la funcionalidad nativa de Adobe Commerce (Mview). Mview realiza una reindexación parcial, que es la forma más eficaz de reindexar los datos. Para obtener más información sobre Mview, consulte [Resumen de la indexación: Mview](https://developer.adobe.com/commerce/php/development/components/indexing/#mview) en nuestra documentación para desarrolladores.

## Lectura relacionada

* [Información general sobre la indexación: cómo reindexar](https://developer.adobe.com/commerce/php/development/components/indexing/#how-to-reindex) en nuestra documentación para desarrolladores.


