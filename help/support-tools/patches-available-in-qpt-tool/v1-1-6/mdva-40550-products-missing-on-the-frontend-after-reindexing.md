---
title: "MDVA-40550: Productos que faltan en el front-end después de la reindexación"
description: El parche MDVA-40550 soluciona el problema de que la reindexación provoca la ausencia de productos en algunas o en todas las categorías de tienda. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6. El ID del parche es MDVA-40550. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: 0aca6eb2-6eb2-4ac4-8ae1-052f671c14e5
feature: Categories, Console, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# MDVA-40550: Productos que faltan en el front-end después de la reindexación

El parche MDVA-40550 soluciona el problema de que la reindexación provoca la ausencia de productos en algunas o en todas las categorías de tienda. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6. El ID del parche es MDVA-40550. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir</u>:

1. Cree un producto.
1. Cambiar indizadores a **Actualizar según la programación**.
   * Asigne el producto a una categoría.
1. Habilite xdebug y realice un punto de interrupción de xdebug en `\Magento\Indexer\Model\Indexer::reindexAll` y `\Magento\Indexer\Model\IndexMutex::execute`.
1. Ejecute **reindexación completa** de `catalog_category_product` con el comando:

   ```bash
   bin/magento indexer:reindex catalog_category_product
   ```

   * Espere a que se detenga la ejecución en el punto de interrupción `\Magento\Indexer\Model\Indexer::reindexAll`.

1. En otra consola, ejecute un **reíndice parcial** en paralelo con el comando:

   ```bash
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Espere a que se detenga la ejecución en el punto de interrupción `\Magento\Indexer\Model\IndexMutex::execute`. Bloqueará el indizador `catalog_category_product`.
1. Reanudar la ejecución del reíndice completo de `catalog_category_product` y esperar un tiempo de espera de bloqueo (60 segundos).

<u>Resultados esperados</u>:

No hay mensajes de error en la consola.

<u>Resultados reales</u>:

Se obtiene el siguiente error:

*No se pudo adquirir el bloqueo para el índice: catalog_category_product.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en nuestra documentación para desarrolladores.
