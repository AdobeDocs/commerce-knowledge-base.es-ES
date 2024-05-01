---
title: "ACSD-49898: La cuadrícula de productos genera una excepción"
description: Aplique el parche ACSD-49898 para corregir el problema de Adobe Commerce en el que la cuadrícula de productos presenta una excepción cuando un producto agrupado tiene un precio especial que supera los 1000.
exl-id: 16a0ec90-7577-46ef-aeb3-a7e9658cf64b
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-49898: La cuadrícula de productos genera una excepción

El parche ACSD-49898 soluciona el problema en el que la cuadrícula de productos genera una excepción cuando un producto agrupado tiene un precio especial que supera los 1000. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 está instalado. El ID del parche es ACSD-49898. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.5-p2

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La cuadrícula de productos genera una excepción cuando un producto agrupado tiene un precio especial que supera los 1000. El problema está relacionado con el uso de comas en lugar de puntos para números decimales en ciertas configuraciones regionales.

<u>Pasos a seguir</u>:

1. Cree un producto agrupado.
1. Establezca el precio especial en 9999; guarde y cierre.
1. Vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Products]**

>[!NOTE]
>
>Busque el SKU del producto agrupado si no está visible.

<u>Resultados esperados</u>:

* El usuario puede filtrar/ver el producto agrupado con el precio especial.
* El precio especial se muestra como porcentaje para productos agrupados y como precio para otros tipos de productos.

<u>Resultados reales</u>:

Se genera el siguiente error: *Valor no numérico encontrado*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
