---
title: "ACSD-50367: La exportación de direcciones de clientes no funciona con atributos de selección múltiple"
description: Aplique el parche ACSD-50367 para solucionar el problema de Adobe Commerce en el que la exportación de direcciones de clientes no funciona cuando se crea un atributo **`Customer Address`** de selección múltiple sin valores.
exl-id: 688831d4-b49e-48fa-b4db-1328cda09a2b
feature: Admin Workspace, Attributes, Data Import/Export, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-50367: La exportación de direcciones de clientes no funciona

El parche ACSD-50367 corrige el problema de que la exportación de direcciones de clientes no funciona cuando se realiza una selección múltiple **`Customer Address`** se crea un atributo sin valores. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 está instalado. El ID del parche es ACSD-50367. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La exportación de direcciones de clientes no funciona cuando se realiza una selección múltiple **`Customer Address`** se crea un atributo sin valores.

<u>Requisitos previos</u>:

Cree un cliente con una dirección.

<u>Pasos a seguir</u>:

1. Crear una selección múltiple **`Customer Address`** atributo en **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer Addresses]**.
1. Ir a **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Export]** y seleccione **`Customer Address`** tipo de entidad.
1. Exportar las direcciones de los clientes. Verá que no se exporta nada.
1. Eliminar la selección múltiple **`Customer Address`** y vuelva a exportar las direcciones de los clientes. Esta vez se genera el archivo CSV de las direcciones.

<u>Resultados esperados</u>:

Las direcciones de clientes se pueden exportar como un archivo CSV cuando se realiza una selección múltiple **`Customer Address`** se ha creado el atributo.

<u>Resultados reales</u>:

Las direcciones de clientes no se pueden exportar como archivo CSV cuando se realiza una selección múltiple **`Customer Address`** se ha creado el atributo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
