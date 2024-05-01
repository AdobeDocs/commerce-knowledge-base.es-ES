---
title: "ACSD-56616: Visualización en la tienda de productos agrupados durante una simple escasez de existencias"
description: Aplique el parche ACSD-56616 para corregir el problema de Adobe Commerce en el que los productos agrupados aparecen inesperadamente en la tienda cuando todos los productos simples asociados están agotados.
feature: Products
role: Admin, Developer
exl-id: 6cf8e15d-38a5-42b6-aee7-67410b501404
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-56616: Visualización de productos agrupados en la tienda durante una simple escasez de existencias.

El parche ACSD-56616 soluciona el problema de que los productos agrupados aparecen inesperadamente en la tienda cuando todos los productos simples asociados están agotados. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 está instalado. El ID del parche es ACSD-56616. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Visualización incorrecta de la tienda de productos empaquetados durante la simple escasez de existencias.

<u>Pasos a seguir</u>:

1. Cree un nuevo sitio web, tienda o tienda.
1. Cree una nueva fuente.
1. Cree un nuevo inventario de stock y asígnelo al sitio web recién creado.
1. Configure los indexadores para que se actualicen según lo programado.
1. Genere dos productos simples, S1 (cantidad = 1) y S2 (cantidad = 1), y asígnelos al nuevo sitio web y a las nuevas existencias.
1. Crear *agrupado1* producto y asociarlo a un nuevo sitio web, colocándolo en la categoría *GATO*.
1. Defina dos opciones desplegables requeridas y vincule un producto simple *S1* a la opción 1 y *S2* a la opción 2.
1. Guarde los productos.
1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** y habilitar *Añadir código de tienda a la URL* = *Sí*.
1. Abra la tienda y compre el producto agrupado.
1. Corre dos veces.
1. Vuelva a la *GATO* categoría.

<u>Resultados esperados</u>:

El *paquete1* el producto está agotado.

<u>Resultados reales</u>:

El *paquete1* el producto es visible con el precio = *$0*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
