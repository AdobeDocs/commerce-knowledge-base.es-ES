---
title: "ACSD-53583: mejorar el rendimiento de reindexación parcial para los indexadores [!UICONTROL Category Products] y [!UICONTROL Product Categories]"
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

El parche ACSD-53583 mejora el rendimiento de reindexación parcial de los indexadores *Category Products* y *Product Categories*. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.39. El ID del parche es ACSD-53583. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p3
* No compatible con el módulo [!DNL Live Search]. Para aplicar esta revisión a la instalación de [!DNL Live Search], solicite una revisión ACSD-55719 adicional.

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La reindexación parcial tarda más que la reindexación completa.

<u>Pasos a seguir</u>:

1. Ponga todos los indexadores en *Actualizar por programación*.
1. Generar datos con [!DNL Performance Toolkit] (perfil medio).
1. Realice cambios en todos los productos y categorías para que estén en el registro de índice pendiente y todos los índices estén inactivos.
1. Realice un reíndice parcial de los indexadores *Category Products* y *Product Categories*.

<u>Resultados esperados</u>:

Se llama a la reindexación parcial una vez por producto y lleva casi el mismo tiempo que la reindexación completa, ya que se cambiaron todos los productos y categorías.

<u>Resultados reales</u>:

Se llama a la reindexación parcial muchas veces por producto y lleva más tiempo que la reindexación completa.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
