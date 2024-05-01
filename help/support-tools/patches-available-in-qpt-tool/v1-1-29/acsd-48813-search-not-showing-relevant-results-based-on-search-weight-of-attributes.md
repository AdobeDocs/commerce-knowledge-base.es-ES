---
title: "ACSD-48813: la búsqueda no muestra resultados relevantes en función del peso de búsqueda de los atributos"
description: Aplique el parche ACSD-48813 para corregir el problema de Adobe Commerce en el que la búsqueda no muestra resultados relevantes en función de la ponderación de búsqueda de los atributos.
exl-id: 089e3ab3-0dfa-4f81-85c7-f6060f326d97
feature: Admin Workspace, Attributes, Search
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-48813: la búsqueda no muestra resultados relevantes en función del peso de búsqueda de los atributos

El parche ACSD-48813 corrige el problema en el que la búsqueda no muestra resultados relevantes en función de la ponderación de búsqueda de los atributos. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 está instalado. El ID del parche es ACSD-48813. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La búsqueda no muestra resultados relevantes en función de la ponderación de búsqueda de los atributos.

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce con datos de ejemplo.
1. Establecer el motor de búsqueda como [!DNL Elasticsearch].
1. Inicie sesión como administrador.
1. Ir a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Products]**.
1. Abra el *name* atributo.
1. Abrir la tienda *[!UICONTROL Properties]* pestaña.
1. Seleccionar [!UICONTROL Search Weight] = *10* en el valor desplegable.
1. Clic **[!UICONTROL Save Attribute]**.
1. Ahora abre la tienda y busca la palabra *Atrás*.

<u>Resultados esperados</u>:

Los productos de mochila se devuelven en la parte superior de los resultados de búsqueda.

<u>Resultados reales</u>:

Los productos de mochila se devuelven en medio de los resultados de búsqueda.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
