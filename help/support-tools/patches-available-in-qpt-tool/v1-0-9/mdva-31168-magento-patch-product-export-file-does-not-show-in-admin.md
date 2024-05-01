---
title: "Parche de MDVA-31168: el archivo de exportación de producto no se muestra en el administrador"
description: El parche MDVA-31168 soluciona el problema de que el archivo CSV de exportación de productos no aparece en la lista de archivos CSV exportables. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10. Tenga en cuenta que el problema se corrigió en la versión 2.4.2 de Adobe Commerce.
exl-id: 780a926b-2aea-47c2-8f95-907cc779bfa4
feature: Admin Workspace, Categories, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# Parche de MDVA-31168: el archivo de exportación de producto no se muestra en el administrador

El parche MDVA-31168 soluciona el problema de que el archivo CSV de exportación de productos no aparece en la lista de archivos CSV exportables. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10 está instalado. Tenga en cuenta que el problema se corrigió en la versión 2.4.2 de Adobe Commerce.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:** Adobe Commerce local 2.3.5-p2.

**Compatible con las versiones de Adobe Commerce:** Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.0 - 2.4.1.

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Requisitos previos</u>:

Instale Adobe Commerce con datos de ejemplo.

<u>Pasos a seguir:</u>

1. Cree un producto descargable y asígnelo a **Bolsas** categoría.
1. Iniciar una exportación para todos los productos.
1. Ejecute el siguiente comando desde CLI:    ```php    bin/magento queue:consumers:start exportProcessor --single-thread --max-messages=10000    ```

<u>Resultados esperados:</u>

El archivo CSV de exportación de productos con todos los productos se muestra en la lista de archivos en Administración, según lo esperado.

<u>Resultados reales:</u>

El archivo CSV de exportación de productos con todos los productos no se muestra en la lista de Administración, aunque el archivo con encabezados solo se generará en la `/var` en el servidor.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
