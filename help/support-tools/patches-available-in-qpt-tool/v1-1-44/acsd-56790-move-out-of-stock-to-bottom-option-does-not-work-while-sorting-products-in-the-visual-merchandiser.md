---
title: 'ACSD-56790: **[!UICONTROL move out of stock to bottom]** opción no funciona al ordenar los productos en  [!DNL Visual Merchandiser]'
description: Aplique el parche ACSD-56790 para corregir el problema de Adobe Commerce en el que la opción Mover fuera de stock a la parte inferior no funciona al ordenar productos en Visual Merchandiser.
feature: Products, Categories
role: Admin, Developer
exl-id: a0c61696-a12d-4c1a-a061-e2f17f38e1f4
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# ACSD-56790: **[!UICONTROL move out of stock to bottom]** La opción no funciona al ordenar productos en [!DNL Visual Merchandiser]

El parche ACSD-56790 soluciona el problema de que la opción Mover del stock al fondo no funciona al ordenar productos en [!DNL Visual Merchandiser]. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 está instalado. El ID del parche es ACSD-56790. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El **[!UICONTROL move out of stock to bottom]** La opción no funciona al ordenar productos en [!DNL Visual Merchandiser]

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce.
1. Ir a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** y cree los atributos siguientes.
1. Crear un nuevo sitio web: **No principal**.
1. Crear un **Almacén que no es principal** en este nuevo sitio web.
1. Cree dos tiendas:

   * Primero en la **Tienda del sitio web principal**.
   * Segundo en la **Almacén que no es principal**.

1. Cree dos fuentes:
   * Cartas.
   * Números.

1. Cree dos existencias:
   * Primer Principal - Canales de ventas: Sitio web principal - Fuentes asignadas: Cartas.
   * Segundo no principal - canales de ventas: no principal - orígenes asignados: números.

1. Cree tres productos simples en ambos sitios web, todos en la categoría predeterminada, todos asignados a ambos orígenes:

   * ProductA - Cantidad *10* en letras, cantidad *0* en Números.
   * Product1 - Cantidad *0* en letras, cantidad *10* en Números.
   * ProductA1 - Cantidad *10* en letras, cantidad *10* en Números.

1. Ir a **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** y seleccione  **[!UICONTROL Default category]**.
1. Cambie el ámbito a **Primero**.
1. Expanda la sección Productos en la categoría.
1. Elija el criterio de ordenación como: **[!UICONTROL move out of stock to bottom]**

<u>Resultados esperados</u>:

La lista de los productos con el **agotado** Los productos de se mueven al final.

<u>Resultados reales</u>:

Los productos no se pueden cargar. Una página redirige al tablero de administración con el siguiente mensaje de error: `Invalid security or form key. Please refresh the page`

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
