---
title: "ACSD-55238: Guardando la metadescripción del producto vacío"
description: Aplique el parche ACSD-55238 para solucionar el problema de Adobe Commerce, donde una descripción del producto que contiene código de HTML generado por [!DNL Page Builder] o cualquier otro editor de HTML se muestra siempre en la descripción meta y no hay forma de configurarlo como empty.
feature: Products, Page Builder, Page Content
role: Admin, Developer
exl-id: 250026c3-925d-4a62-9855-d892c86d3d24
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-55238: Guardar la metadescripción vacía del producto

El parche ACSD-55238 corrige el problema de que siempre se muestra en la metadescripción una descripción de producto que contiene código de HTML generado por un editor de HTML. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 está instalado. El ID del parche es ACSD-55238. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Una descripción del producto que contiene código de HTML generado por [!DNL Page Builder] o cualquier otro editor de HTML se muestra siempre en la descripción meta y no hay forma de configurarlo como empty.

<u>Pasos a seguir</u>:

1. Ir a **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Block]** y cree un nuevo bloque con cualquier contenido.
1. Ir a **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product]** y cree un nuevo producto. Establezca la metadescripción en empty.
1. Añada el bloque creado anteriormente mediante *[!DNL Page Builder]* en el *[!UICONTROL Content]* y guarde el producto.
1. Abra el producto en la tienda y compruebe su elemento doc `meta name = "description"`.

<u>Resultados esperados</u>:

La metadescripción está vacía.

<u>Resultados reales</u>:

Cuando un producto tiene un bloque en su descripción, se utiliza para la metadescripción del producto.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
