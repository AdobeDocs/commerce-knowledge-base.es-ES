---
title: "ACSD-45255: Excepción en la página de informe de Stock bajo para el usuario administrador restringido"
description: El parche ACSD-45255 resuelve el problema en el que se produce una excepción en la página Informe de bajo stock para un usuario administrador restringido. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18. El ID del parche es ACSD-45255. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.
exl-id: 4b08500a-384e-4d5b-9563-3f9d1b984349
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-45255: Excepción en la página de informe de Stock bajo para el usuario administrador restringido

El parche ACSD-45255 resuelve el problema en el que se produce una excepción en la página Informe de bajo stock para un usuario administrador restringido. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 está instalado. El ID del parche es ACSD-45255. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se produce una excepción en la página Informe de existencias bajas para un usuario administrador restringido.

<u>Requisitos previos</u>:

* Los módulos de inventario están habilitados.
* Hay un sitio web, una tienda y una vista de la tienda adicionales.
* Hay un usuario administrador restringido con acceso solo al sitio web adicional.

<u>Pasos a seguir</u>:

1. Abra el Administrador de Commerce como usuario administrador restringido.
1. Ir a **Informes** > **Productos** > **Stock bajo**.

<u>Resultados esperados</u>:

Se muestra el informe Stock bajo para el usuario administrador restringido.

<u>Resultados reales</u>:

Se genera una excepción:

```bash
TypeError: Argument 1 passed to Magento\InventoryLowQuantityNotification\Model\ResourceModel\LowQuantityCollection\Interceptor::addStoreFilter() must be of the type int, array given, called in ../app/code/Magento/AdminGws/Plugin/CollectionFilter.php on line 101 and defined in ../generated/code/Magento/InventoryLowQuantityNotification/Model/ResourceModel/LowQuantityCollection/Interceptor.php:20
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
