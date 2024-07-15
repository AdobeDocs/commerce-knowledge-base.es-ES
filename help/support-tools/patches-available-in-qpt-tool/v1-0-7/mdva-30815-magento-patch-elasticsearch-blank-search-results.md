---
title: 'MDVA-30815: resultados de búsqueda en blanco del Elasticsearch'
description: El parche MDVA-30815 corrige el problema en el que Elasticsearch muestra una página en blanco cuando se cambian las opciones del limitador de los resultados de búsqueda. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.3.5.
exl-id: dbe41a43-e248-407e-8cf9-319ad5843935
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-30815: resultados de búsqueda en blanco del Elasticsearch

El parche MDVA-30815 corrige el problema en el que Elasticsearch muestra una página en blanco cuando se cambian las opciones del limitador de los resultados de búsqueda. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.3.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce en infraestructura en la nube 2.3.3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al utilizar el Elasticsearch, si cambia las opciones del limitador de los resultados de búsqueda, Adobe Commerce muestra una página en blanco.

<u>Requisitos previos</u>:

El Elasticsearch está **habilitado**. Vaya a **TIENDAS** > **Configuración** > **Configuración** > **Catálogo** > **Búsqueda en el catálogo**.

<u>Pasos a seguir</u>:

1. Vaya a su sitio.
1. Busque un producto en el campo de búsqueda principal.
1. Una vez mostradas las páginas de resultados de búsqueda, haga clic en la última página de las páginas de resultados de búsqueda.
1. Seleccione **Mostrar xx por página** en la opción de limitador. Asegúrese de que este es un límite de número de resultados de búsqueda diferente al configurado actualmente.

<u>Resultados esperados</u>:

La página muestra el número configurado de resultados del producto.

<u>Resultados reales</u>:

Se muestra una página en blanco. Este error también se puede ver en `var/report` : *\`&quot;0&quot;:&quot;SQLSTATE\[42000\]: Error de sintaxis o infracción de acceso: 1064 Tiene un error en la sintaxis SQL; consulte el manual correspondiente a su versión del servidor MySQL para ver la sintaxis correcta para usar cerca de&#39;\`*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
