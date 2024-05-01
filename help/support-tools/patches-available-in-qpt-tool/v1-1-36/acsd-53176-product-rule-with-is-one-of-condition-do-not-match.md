---
title: '"ACSD-53176: La regla de producto con "es una de" condición no coincide"'
description: Aplique el parche ACSD-53176 para solucionar el problema de Adobe Commerce donde la regla de producto relacionada `is one of` no funciona correctamente para "Productos que coinciden".
feature: Marketing Tools
role: Admin
exl-id: 91f05f5b-6a5e-4b93-9dfb-88cbeccb6c9e
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-53176: Regla de producto con `is one of` la condición no coincide

El parche ACSD-53176 corrige el problema en el que la regla de producto relacionada `is one of` la condición no funciona correctamente para **Productos para hacer coincidir**. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.36 está instalado. El ID del parche es ACSD-53176. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La regla de producto relacionada `is one of` la condición no funciona correctamente para **Productos para hacer coincidir**.

<u>Pasos a seguir</u>:

1. Cree de 3 a 4 productos.
1. Cree una nueva regla de producto relacionada.

   Configure la regla para que coincida con dos o más productos:
   * `SKU is one of "S1,S2".`

   Configure la regla para que muestre dos o más elementos:
   * `Product SKU is one of constant value "S2,S3".`

1. Abra el producto S1 en la Tienda.

<u>Resultados esperados</u>:

Los productos relacionados &quot;S2&quot; y &quot;S3&quot; se muestran en las páginas de productos &quot;S1&quot; y &quot;S2&quot;.

<u>Resultados reales</u>:

Los productos relacionados no se muestran en las páginas de productos de.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
