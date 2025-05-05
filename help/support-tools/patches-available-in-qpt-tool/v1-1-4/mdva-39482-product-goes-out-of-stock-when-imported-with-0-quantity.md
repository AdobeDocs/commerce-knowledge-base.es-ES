---
title: "MDVA-39482: El producto se queda sin existencias si se importa con una cantidad '0' con los pedidos pendientes habilitados"
description: El MDVA-39482 corrige el problema en el que el producto se queda sin existencias si se importa con una cantidad "0" cuando MSI y los pedidos no satisfechos están activados y el umbral de falta de existencias se establece en un valor negativo. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4. El ID del parche es MDVA-39482. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: 2caf461c-993d-48b3-bc47-3fa1d014deaf
feature: Data Import/Export, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-39482: El producto se queda sin existencias si se importa con una cantidad &quot;0&quot; con los pedidos pendientes habilitados

El MDVA-39482 corrige el problema en el que el producto se queda sin existencias si se importa con una cantidad &quot;0&quot; cuando MSI y los pedidos no satisfechos están activados y el umbral de falta de existencias se establece en un valor negativo. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4. El ID del parche es MDVA-39482. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.1-p1

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El producto se queda sin existencias si se importa con una cantidad &quot;0&quot; cuando MSI y los pedidos no satisfechos están activados y el umbral Agotado se establece en un valor negativo.

<u>Requisitos previos</u>:

1. Se deben instalar MSI y datos de ejemplo.
1. Vaya a **Tiendas** > **Configuraciones** > **Catálogo** > **Inventario**:
   * Establecer pedidos pendientes en &quot;Permitir cantidad inferior a 0&quot;
   * Establezca el umbral de falta de stock en &quot;-10&quot;

<u>Pasos a seguir</u>:

1. Asegúrese de que el SKU esté **en existencia** y que tenga la cantidad **24-MB01**.
1. Importe el CSV de las fuentes de stock. Asegúrese de seleccionar &quot;Fuentes de stock&quot; en Tipo de entidad:

   ```code panel
   sku,qty,out_of_stock_qty
   24-MB01,0,-10
   ```

1. Compruebe el estado de las existencias del producto una vez importadas las fuentes de existencias.

<u>Resultados esperados</u>:

El MB01 de 24 es **En stock** en Storefront.

<u>Resultados reales</u>:

El MB01 de 24 está **agotado** en Storefront.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/usage) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
