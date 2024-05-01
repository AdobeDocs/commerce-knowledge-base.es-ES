---
title: "ACSD-51114: Los productos aleatorios desaparecieron de los catálogos grandes cuando la indexación asíncrona está habilitada"
description: Aplique el parche ACSD-51114 para solucionar el problema de Adobe Commerce Los productos aleatorios desaparecieron de los catálogos grandes cuando la indexación asíncrona está habilitada.
exl-id: 6ea7de32-1d30-4c4a-af6e-6a0931396846
feature: Catalog Management, Categories, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51114: Los productos aleatorios desaparecieron de los catálogos grandes cuando la indexación asíncrona está habilitada

>[!NOTE]
>
>Este parche está obsoleto.

El parche ACSD-51114 corrige el problema Los productos aleatorios desaparecieron de los catálogos grandes cuando la indexación asíncrona está habilitada. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 está instalado. El ID del parche es ACSD-51114. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la última versión y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]:Página Buscar Parches].Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los productos aleatorios desaparecían de los catálogos grandes cuando la indexación asíncrona estaba activada.

<u>Pasos a seguir</u>:

1. Cree un conjunto de 10 productos.
1. Establezca todos los indexadores en **[!UICONTROL Update on Save]** modo.
1. Cree una categoría y asígnele todos los productos.
1. Desactive todos los productos.
1. Abra la categoría y compruebe que no hay productos allí.
1. Establezca todos los indexadores en **[!UICONTROL Update on Schedule]** modo.
1. Configure las variables `DEFAULT_BATCH_SIZE` a 2 pulgadas  `lib/internal/Magento/Framework/Mview/View.php#L31`.
1. Active los productos en el siguiente orden: 1º, 9º, 2º, 5º, 10º, 3º.
1. Ejecute el comando cron.
1. Abra la categoría de nuevo.

<u>Resultados esperados</u>:

Se muestran todos los productos habilitados.

<u>Resultados reales</u>:

No se muestran todos los productos habilitados.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
