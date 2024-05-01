---
title: "MDVA-33453: La previsualización de Page Builder rompe los precios del producto y difiere entre sitios"
description: El parche MDVA-33453 resuelve el problema de que la previsualización de Page Builder se interrumpe si los productos coincidentes tienen un precio diferente para cada sitio web. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.
exl-id: 78a7f7d4-8691-4b5d-a900-1c9a6ec73486
feature: CMS, Orders, Page Builder, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-33453: Saltos de vista previa del Page Builder: el precio del producto difiere entre los sitios

El parche MDVA-33453 resuelve el problema de que la previsualización de Page Builder se interrumpe si los productos coincidentes tienen un precio diferente para cada sitio web. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 está instalado. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:** Adobe Commerce en la infraestructura en la nube 2.4.1

**Compatible con las versiones de Adobe Commerce:** Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.6 - 2.4.1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La vista previa del producto Page Builder se interrumpe cuando hay un producto con diferentes precios en diferentes sitios web.

<u>Pasos a seguir</u>:

1. Inicie sesión en el panel de administración de Commerce.
1. Cree dos sitios web.
1. Cree un producto sencillo.
1. Establezca un precio diferente para el producto en cada sitio web.
1. Ejecute cron y vuelva a indexar.
1. Cree o edite una página de CMS y utilice el bloque de producto para añadir el producto.

<u>Resultado real</u>:<br>

Se produce el siguiente error:

*Error filtering template: Ya existe un elemento (Magento\\Catalog\\Model\\Product\\Interceptor) con el mismo ID &quot;2&quot;.*

<u>Resultado esperado</u>:<br>

No se muestran errores.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
