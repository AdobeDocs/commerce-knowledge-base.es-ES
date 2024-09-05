---
title: "ACSD-59378: Store-level [!DNL URL] reescribe incorrectamente actualizado durante la importación"
description: Aplique el parche ACSD-59378 para corregir el problema de Adobe Commerce donde las reescrituras a nivel de tienda [!DNL URL] se actualizan incorrectamente durante la importación.
feature: Data Import/Export
role: Admin, Developer
source-git-commit: 3f400c3e325c3f377a5e12170b08615ebeadbcd1
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---


# ACSD-59378: las reescrituras a nivel de tienda [!DNL URL] se actualizaron incorrectamente durante la importación

La revisión ACSD-59378 corrige el problema en el que las reescrituras en el nivel de almacén [!DNL URL] se actualizan incorrectamente durante la importación. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50. El ID del parche es ACSD-59378. Tenga en cuenta que este problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.5-p5

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.5x (todas las versiones de 2.4.5)

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las reescrituras a nivel de tienda [!DNL URL] se actualizaron incorrectamente durante la importación.

<u>Pasos a seguir</u>:

1. Cree un producto con `url_key = key_default` en el ámbito **Todas las vistas de la tienda**.
1. Establezca `url_key = key_store` en el ámbito **Vista de tienda predeterminada**.
1. Exporte el producto.
1. Importar un archivo de [!DNL CSV] para este producto con los siguientes datos:
   * La columna `store_view_code` se ha establecido en *vacío* para que se aplique al ámbito **Todas las vistas de la tienda**.
   * `url_key` está establecido en la clave predeterminada *`key_default`*.

<u>Resultados esperados</u>:

Las reescrituras de [!DNL URL] solo se regeneran para las vistas de tienda donde no haya `url_key` anulado (donde se aplica el valor predeterminado `url_key`).

<u>Resultados reales</u>:

Se eliminan las reescrituras de `key_store` [!DNL URL], pero la reescritura de [!DNL URL] en el nivel de **Vista de tienda predeterminada** para el producto sigue establecida en *`key_store`*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].