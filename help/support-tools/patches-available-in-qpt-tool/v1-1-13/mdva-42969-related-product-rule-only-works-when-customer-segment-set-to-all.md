---
title: "MDVA-42969: La regla de producto relacionada solo funciona cuando el segmento de cliente está configurado en todo"
description: El parche MDVA-42969 corrige el problema de que la regla de producto relacionada solo funciona cuando el segmento de cliente está configurado en todo. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. El ID del parche es MDVA-42969. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: 2877ba7a-2681-4de2-9c37-228de232424f
feature: Customer Service, Marketing Tools, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# MDVA-42969: La regla de producto relacionada solo funciona cuando el segmento de cliente está configurado en todo

El parche MDVA-42969 corrige el problema de que la regla de producto relacionada solo funciona cuando el segmento de cliente está configurado en todo. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. El ID del parche es MDVA-42969. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La regla de producto relacionada solo funciona cuando el segmento de cliente está establecido en todo.

<u>Pasos a seguir</u>:

1. Vaya a **Tiendas** > **Configuración** > **Catálogo** > **Relaciones de producto basadas en reglas** y establezca **Mostrar productos relacionados** = **Solo basados en reglas**.
1. Vaya a **Clientes** > **Segmentos** y cree un nuevo segmento: **Aplicar a** = **Visitantes y clientes registrados**.
1. Vaya a **Marketing** > **Reglas de producto relacionadas** y cree una regla nueva.

   ```code block
   Apply To = Related Products
   Customer Segments = All
   Products to Match = SKU = <select a SKU>
   Products to Display = SKU +is one of+ Constant Value (specify 1-3 products)
   ```

1. Abra el producto coincidente en la tienda y compruebe que se muestran los productos que se van a mostrar.
1. Modifique la regla creada en el paso tres y establezca **Segmentos del cliente** = **Específico** > **Segmento** del paso dos.
1. Abra el producto coincidente en la tienda.

<u>Resultados esperados</u>:

Los productos relacionados basados en reglas se muestran en la tienda para los visitantes del producto porque el segmento de clientes se crea con la siguiente configuración:

**Aplicar a** = **Visitantes y clientes registrados**

<u>Resultados reales</u>:

No se muestran productos relacionados.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/usage) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en nuestra documentación para desarrolladores.
