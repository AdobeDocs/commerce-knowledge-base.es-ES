---
title: "ACSD-47054: previsualizar contenido lento mientras todas las tiendas reindexan"
description: Aplique el parche ACSD-47054 para corregir el problema de Adobe Commerce en el que la página de vista previa tarda en cargarse debido al reíndice de todas las tiendas.
feature: Page Content
role: Admin, Developer
exl-id: 4dc61f78-7038-48ab-a2d3-9b05cf0c9b5c
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-47054: previsualizar contenido lento mientras todas las tiendas reindexan

El parche ACSD-47054 soluciona el problema de que una vista previa de la puesta en escena del contenido tarda más en cargarse cuando hay muchas tiendas. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.37 está instalado. El ID del parche es ACSD-47054. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación): 2.4.2-p2, 2.4.5-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación): 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La página de vista previa tarda mucho tiempo en cargarse debido a una reindexación de todas las tiendas.

<u>Pasos a seguir</u>:

1. Vaya al Administrador de Commerce.
1. Cree cualquier actualización programada.
1. Ir a **[!UICONTROL Content]** > **[!UICONTROL Dashboard]**.
1. Previsualice la actualización programada.
1. Abra cualquier categoría.

<u>Resultados esperados</u>:

La página de vista previa se carga en un plazo de tiempo aceptable.

<u>Resultados reales</u>:

La previsualización del ensayo del contenido está tardando mucho tiempo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
