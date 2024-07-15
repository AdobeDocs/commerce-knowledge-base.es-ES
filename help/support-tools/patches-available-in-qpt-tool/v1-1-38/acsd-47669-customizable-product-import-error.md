---
title: "ACSD-47669: Error interno del servidor al importar productos con opciones personalizables"
description: Aplique el parche ACSD-47669 para corregir el problema de Adobe Commerce en el que hay un error interno del servidor durante la importación de productos con opciones personalizables.
feature: Products
role: Admin, Developer
exl-id: 14afbd71-075a-4264-8da2-dbbd93f472a1
source-git-commit: 66e56b9ba31fd2c5d3f8a330f09d8e94df77b17d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-47669: Error interno del servidor al importar productos con opciones personalizables

El parche ACSD-47669 corrige el problema en el que hay un error interno del servidor durante las importaciones de productos con opciones personalizables. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.38. El ID del parche es ACSD-47669. Tenga en cuenta que el problema ya se ha corregido en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se ha producido un error interno del servidor al importar productos con opciones personalizables.

<u>Pasos a seguir</u>:

1. Crear una vista de tienda adicional. Asegúrese de tener dos vistas de la tienda, por ejemplo, en o Reino Unido.
1. Cree dos productos simples, por ejemplo, prod1 y prod2.
1. Prepare un archivo .csv que agregue opciones personalizadas para ambos productos en cada vista de tienda y para el ámbito **Todas las vistas de tienda**. Importe este archivo CSV.
1. Prepare otro archivo csv que incluya dos registros. El primer registro debe ser para actualizar las opciones personalizadas de &#39;prod1&#39; específicamente para el ámbito de la vista de tienda del Reino Unido y el segundo registro debe ser para actualizar las opciones personalizadas de &#39;prod2&#39; para el ámbito **Toda la vista de tienda**. Importe este segundo archivo CSV.

<u>Resultados esperados</u>:

Debería poder personalizar las opciones sin ningún error.

<u>Resultados reales</u>:

Se produce un error de infracción de restricción de integridad.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
