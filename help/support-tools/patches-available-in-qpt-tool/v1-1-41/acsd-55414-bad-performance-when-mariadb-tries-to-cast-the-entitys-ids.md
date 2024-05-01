---
title: "ACSD-55414: Rendimiento incorrecto cuando MariaDB intenta convertir entitys_ids"
description: Aplique el parche ACSD-55414 para solucionar el problema de Adobe Commerce cuando MariaDB intente convertir entitys_ids de cadena a entero, lo que dificulta el rendimiento de la reindexación.
feature: Attributes
role: Admin, Developer
exl-id: 008a4fda-5d80-47e2-8fb4-c1e39d15a6ba
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-55414: mal rendimiento cuando MariaDB intenta convertir el `entitys_ids`

El parche ACSD-55414 corrige el problema en el que el rendimiento de la reindexación se ve obstaculizado cuando MariaDB intenta convertir `entitys_ids` de cadena a entero. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.41 está instalado. El ID del parche es ACSD-55414. Tenga en cuenta que el problema se corrige en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El rendimiento de la reindexación se ve obstaculizado cuando MariaDB intenta convertir el `entitys_ids` de cadena a entero.

<u>Pasos a seguir</u>:

1. Actualizar `setup/performance-toolkit/profiles/ce/small.xml` mediante la configuración de *50000* productos simples.
1. Genere este perfil ejecutando el comando: `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Ejecutar reindexación: `bin/magento indexer:reindex catalog_product_attribute`.

<u>Resultados esperados</u>:

La reindexación tarda un tiempo razonable en completarse.

<u>Resultados reales</u>:

La reindexación tarda demasiado en completarse.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
