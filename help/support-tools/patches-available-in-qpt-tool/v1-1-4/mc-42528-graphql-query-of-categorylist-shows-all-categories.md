---
title: "MC-42528: la consulta GraphQL de categoryList muestra todas las categorías"
description: El parche MC-42528 resuelve el problema en el que la consulta GraphQL de categoryList devuelve categorías asignadas y no asignadas cuando la categoría de navegación de una categoría en particular está establecida en Denegar. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4. El ID del parche es MC-42528. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: 8bb29f43-92ae-4f37-b147-7121b55c185b
feature: Catalog Management, Categories, GraphQL, Customer Service
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MC-42528: la consulta GraphQL de categoryList muestra todas las categorías

El parche de MC-42528 resuelve el problema en el que la consulta GraphQL de `categoryList` devuelve categorías asignadas y no asignadas cuando la categoría de exploración de una categoría en particular está establecida en &quot;Denegar&quot;. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4. El ID del parche es MC-42528. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La consulta GraphQL de `categoryList` devuelve categorías asignadas y no asignadas.

<u>Pasos a seguir</u>:

1. Cree dos categorías, CAT1 y CAT2, y asigne pocos productos a cada categoría.
1. Cree un catálogo compartido privado.
1. Cree un usuario de empresa y asígnelo al catálogo compartido creado.
1. Asigne CAT1 al catálogo personalizado y establezca el permiso de categoría en &quot;Permitir&quot; categoría de navegación para el grupo de clientes del catálogo privado.
1. Defina el permiso de categoría para CAT2 en &quot;Denegar&quot; categoría de navegación para el grupo de clientes del catálogo privado.
1. Ejecute la consulta de GraphQL `categoryList` o `categories` como usuario de la compañía.

<u>Resultados esperados</u>:

En la respuesta solo aparece el CAT1.

<u>Resultados reales</u>:

Todas las categorías aparecen en la respuesta independientemente de los permisos de exploración de la categoría.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/usage) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
