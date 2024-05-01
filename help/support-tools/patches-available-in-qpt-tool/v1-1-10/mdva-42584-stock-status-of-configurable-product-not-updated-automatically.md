---
title: "MDVA-42584: El estado de stock del producto configurable no se actualiza automáticamente"
description: El parche MDVA-42584 resuelve el problema en el que el estado de stock del producto configurable no se actualiza automáticamente cuando se actualiza su producto simple. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10. El ID del parche es MDVA-42584. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: bf2697a2-8d15-408b-8d59-7b4173537e60
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# MDVA-42584: El estado de stock del producto configurable no se actualiza automáticamente

El parche MDVA-42584 resuelve el problema en el que el estado de stock del producto configurable no se actualiza automáticamente cuando se actualiza su producto simple. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 está instalado. El ID del parche es MDVA-42584. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El estado de stock del producto configurable en el servidor no se actualiza automáticamente cuando su producto simple se establece en **En stock** mediante API o importación.

<u>Requisitos previos</u>:

MSI instalado.

<u>Pasos a seguir</u>:

1. Crear un producto configurable, **InvCheck001**, con dos opciones: **InvCheck001-M** y **InvCheck001-L**.
1. Ambos productos simples deben tener Cantidad y deben tener **En stock** para que el producto configurable también **En stock** en el servidor.
1. Ahora, actualice ambos productos simples y establezca Cantidad en **0** y el estado de Stock a **Sin existencias**.
1. Actualice el producto configurable y verifique que el estado de las existencias se actualice a **Sin existencias**.
1. Utilice el siguiente punto de conexión de API y configure el producto simple **InvCheck001-M** hasta **En stock** con Cantidad > 0.

   ```JSON
   /rest/V1/inventory/source-items
   
   {
     "sourceItems":
     [
       {
         "sku": "InvCheck001-M",
         "source_code": "default",
         "quantity": 10,
         "status": 1
       }
     ]
   }
   ```

1. Vaya al servidor y verifique la cantidad y el estado de stock del producto simple **InvCheck001-M**. Se ha actualizado a **En stock**.
1. Actualice el producto configurable y compruebe el estado de las existencias.

<u>Resultados esperados</u>:

El estado de stock del producto configurable **InvCheck001** en el servidor se actualiza automáticamente a **En stock**.

<u>Resultados reales</u>:

El estado de stock del producto configurable sigue siendo **Sin existencias**.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
