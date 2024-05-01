---
title: "MDVA-31590: No se pueden actualizar atributos por lotes mediante colas asincrónicas de MySQL"
description: El parche MDVA-31590 resuelve el problema en el que los usuarios no pueden actualizar los atributos de forma masiva mediante colas asincrónicas de MySQL. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3. El ID del parche es MDVA-31590. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.
exl-id: 57db28dd-a739-4a77-927d-6339af4fa4a6
feature: Attributes, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 0%

---

# MDVA-31590: No se pueden actualizar atributos por lotes mediante colas asíncronas de MySQL

El parche MDVA-31590 resuelve el problema en el que los usuarios no pueden actualizar los atributos de forma masiva mediante colas asincrónicas de MySQL. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3 está instalado. El ID del parche es MDVA-31590. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0-2.4.1-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios no pueden actualizar los atributos de forma masiva mediante MySQL asincrónico.

<u>Pasos a seguir</u>:

1. En la cuadrícula de productos del servidor, realice una acción masiva para actualizar los valores de atributo de algunos productos.
   * Compruebe los productos y seleccione **Actualizar atributos** en el menú desplegable Acciones.
1. Establezca valores para los atributos necesarios, asigne productos a sitios web y guárdelos.
1. Una vez que la página se vuelve a cargar, muestra un mensaje como el siguiente:
   *Tarea &quot;Actualizar atributos para N productos seleccionados&quot;: Se ha programado 1 artículo(s) para una actualización.*
1. Espere unos segundos y vuelva a cargar la página back-end.

<u>Resultados esperados</u>:

1. La página muestra un mensaje de actualización correcta como: *1 elemento(s) se ha(n) actualizado correctamente.*
1. Se actualizan los valores de atributo de los productos relacionados.
1. En la base de datos, los nuevos registros se crean en ambos `magento_bulk` tabla y `magento_operation` tabla (operaciones relacionadas con el lote).
1. Los registros nuevos se crean en la variable `queue_message` tabla (relacionada con las colas) `product_action_attribute.update` y/o `product_action_attribute.website.update`).
1. `queue_message_status` tiene registros con el estado &quot;4&quot;.
1. NO hay errores en `system.log`.

<u>Resultados reales</u>:

1. La página sigue mostrando un mensaje como el siguiente:
   *Tarea &quot;Actualizar atributos para N productos seleccionados&quot;: Se ha programado 1 artículo(s) para una actualización.*
1. Se actualizan los valores de atributo de los productos.
1. Se crea un nuevo registro en `message_bulk` tabla, pero no hay ningún registro relacionado en `magento_operation` tabla.
1. Los registros nuevos se crean en `queue_message` y `queue_message_status` tablas.
1. `queue_message_status` la tabla tiene un registro con estado de error (valor de estado &quot;6&quot;).
1. `system.log` contiene un error similar al siguiente:
   *main.CRITICAL: se ha rechazado el mensaje: SQLSTATE[23000]: infracción de restricción de integridad: 1048 La columna &#39;operation_key&#39; no puede ser nula, la consulta era: INSERT INTO {{magento_operation}} ({{id}}, {{bulk_uuid}}, {{topic_name}}, {{serialized_data}}, {{result_serialized_data}}, {{status}}, {{error_code}}, {{result_message}}, {{operation_key}}) VALORES (?, ?, ?, ?, ?, ?, ?, ?) [][]*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sección.
