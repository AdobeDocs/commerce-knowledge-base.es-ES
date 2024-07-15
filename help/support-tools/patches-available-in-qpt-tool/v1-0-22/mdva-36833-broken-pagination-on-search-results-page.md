---
title: "MDVA-36833: paginación rota en la página de resultados de búsqueda"
description: El parche MDVA-36833 corrige el problema de que la paginación se interrumpe cuando el catálogo compartido está habilitado y algunos productos se han excluido del catálogo compartido. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22. El ID del parche es MDVA-36833. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.
exl-id: 7105c4ed-48d9-4d4c-bf12-5914bbad62da
feature: Catalog Management, Search
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-36833: paginación rota en la página de resultados de búsqueda

El parche MDVA-36833 corrige el problema de que la paginación se interrumpe cuando el catálogo compartido está habilitado y algunos productos se han excluido del catálogo compartido. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22. El ID del parche es MDVA-36833. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:** Adobe Commerce (todos los métodos de implementación) 2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La exclusión de algunos productos del catálogo compartido provoca que se interrumpa la paginación de los resultados de búsqueda.

<u>Pasos a seguir:</u>

1. Habilitar catálogo compartido.
1. Vaya a **Catálogo** > **Catálogos compartidos** y configure el catálogo compartido predeterminado asignándole todos los productos.
1. Cargue la tienda y busque &quot;chaqueta&quot;.
1. Observe los productos que aparecen en la primera página. Debe haber 12 productos.
1. Anote 11 SKU desde la primera página. Vaya al servidor y cargue el catálogo compartido predeterminado.
1. Anule la asignación de las SKU anotadas anteriormente del catálogo compartido predeterminado.
1. Ve a la tienda y busca &quot;chaqueta&quot;.
1. Compruebe la primera página de los resultados de búsqueda.

<u>Resultado real:</u>

La primera página tiene un producto y los demás productos están disponibles en la segunda página.

<u>Resultado esperado:</u>

La primera página debe tener 12 productos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.


## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
