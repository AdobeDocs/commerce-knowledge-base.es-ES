---
title: '"ACSD-53583: Mejora del rendimiento de reindexación parcial para [!UICONTROL Category Products] y [!UICONTROL Product Categories] de indexadores'
description: Aplique el parche ACSD-53585 para mejorar el rendimiento de reindexación parcial para los indexadores de productos de categoría y de categorías de productos.
feature: Products, Categories
role: Admin, Developer
exl-id: 1c8f7df3-379f-42d6-8b41-286d34f725d2
source-git-commit: 29c2918ccae6404f6ae87d360ac16b149de5dd0d
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-53583: mejore el rendimiento de reindexación parcial para los indexadores de Productos de categoría y Categorías de productos

El parche ACSD-53583 mejora el rendimiento de reindexación parcial de *Productos de categoría* y *Categorías de productos* indexadores. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.39 está instalado. El ID del parche es ACSD-53583. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p3
* No compatible con [!DNL Live Search] módulo. Para aplicar este parche a [!DNL Live Search] instalación, solicite un parche ACSD-55719 adicional.

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La reindexación parcial tarda más que la reindexación completa.

<u>Pasos a seguir</u>:

1. Convertir todos los indizadores a *Actualizar según lo programado*.
1. Generar datos con [!DNL Performance Toolkit] (perfil medio).
1. Realice cambios en todos los productos y categorías para que estén en el registro de índice pendiente y todos los índices estén inactivos.
1. Realizar reindexación parcial para *Productos de categoría* y *Categorías de productos* indexadores.

<u>Resultados esperados</u>:

Se llama a la reindexación parcial una vez por producto y lleva casi el mismo tiempo que la reindexación completa, ya que se cambiaron todos los productos y categorías.

<u>Resultados reales</u>:

Se llama a la reindexación parcial muchas veces por producto y lleva más tiempo que la reindexación completa.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
