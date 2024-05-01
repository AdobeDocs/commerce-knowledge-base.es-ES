---
title: "ACSD-52815: El campo de entrada para el campo de cantidad de origen no predeterminado solo admite hasta 6 dígitos"
description: Aplique el parche ACSD-52815 para solucionar el problema de rendimiento de Adobe Commerce, donde el campo de entrada del campo de cantidad de un origen no predeterminado solo admite hasta 6 dígitos, a diferencia de 8 para un stock predeterminado.
feature: Inventory, Products
role: Admin
exl-id: 44fda5ef-cb8a-481a-9112-f36d886ae3db
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-52815: el campo de entrada para el campo de cantidad de origen no predeterminado solo admite hasta 6 dígitos

El parche ACSD-52815 corrige el problema en el que el campo de entrada del campo de cantidad de una fuente no predeterminada solo admite hasta 6 dígitos, a diferencia de 8 para una acción predeterminada. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.35 está instalado. El ID del parche es ACSD-52815. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El campo de entrada para el campo de cantidad de un origen no predeterminado solo admite hasta 6 dígitos, a diferencia de 8 para un stock predeterminado.

<u>Pasos a seguir</u>:

1. Cree un nuevo stock y un nuevo origen.
1. Cree un producto con el nuevo stock de origen establecido en 123.
1. Comprobar la cantidad salable (123).
1. Actualice la cantidad de origen a 12345678.
1. Vuelva a comprobar la cantidad vendible.

<u>Resultados esperados</u>:

La cantidad vendible muestra la cantidad correcta.

<u>Resultados reales</u>:

La cantidad vendible es de 999999.9999.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
