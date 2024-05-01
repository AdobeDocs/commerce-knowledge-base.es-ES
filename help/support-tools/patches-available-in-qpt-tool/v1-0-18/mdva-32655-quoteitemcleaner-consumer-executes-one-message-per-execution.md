---
title: '"MDVA-32655: "quoteItemCleaner" consumidor ejecuta un mensaje por ejecución"'
description: El parche MDVA-32655 corrige el estado incorrecto del mensaje "en curso" al mensaje "completo" correcto para el consumidor `quoteItemCleaner` después de eliminar varios productos. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18. El ID del parche está 32655. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.
exl-id: 07213430-f779-4a53-89fd-bc3905e13675
feature: Quotes
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-32655: El consumidor &quot;quoteItemCleaner&quot; ejecuta un mensaje por ejecución

El parche MDVA-32655 corrige el estado incorrecto del mensaje &quot;en curso&quot; al mensaje &quot;completo&quot; correcto para el consumidor `quoteItemCleaner` después de eliminar varios productos. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 está instalado. El ID del parche está 32655. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.3

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.0 - 2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El `quoteItemCleaner` El cliente solo ejecuta un mensaje en cada ejecución.

<u>Pasos a seguir</u>:

1. Compruebe la `queue_message_status` tabla de la base de datos y asegúrese de que todos los mensajes en cola existentes están en el estado &quot;Completado&quot; (ID de estado 4).
1. Detener la ejecución automática de Adobe Commerce cron.
1. Cree dos o tres productos simples.
1. Haga una eliminación masiva de esos tres productos simples.
1. En el `queue_message_status` tabla puede ver que hay tres registros nuevos para el `catalog_product_removed_queue` tema con ID de estado 2 (nuevo registro).
1. Ejecute el siguiente comando para procesar estos pendientes `catalog_product_removed_queue` mensajes:

   ```bash
   bin/magento queue:consumers:start quoteItemCleaner --single-thread --max-messages=100
   ```

<u>Resultados esperados</u>:

```sql
select * from queue_message_status s join queue q on s.queue_id = q.id where q.name = "catalog_product_removed_queue";
```

Todos los `catalog_product_removed_queue` los estados de los mensajes se actualizan para completarse (ID=4).

<u>Resultados reales</u>:

Solo un registro de los tres se actualiza al estado &quot;Completado&quot; (ID = 4). El estado de los otros dos mensajes es ID de estado = 3 (en curso). Se genera un registro de pendientes con los mensajes en cola no procesados.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
