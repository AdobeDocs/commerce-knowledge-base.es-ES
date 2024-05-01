---
title: "MDVA-44940: Error SQL al guardar la categoría del administrador"
description: El parche MDVA-44940 corrige el problema en el que se produce un error SQL al guardar una categoría del administrador. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16. El ID del parche es MDVA-44940. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.
exl-id: cae6f231-3b91-441f-af56-824db0fa2d32
feature: Admin Workspace, Categories, Sales Channels
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# MDVA-44940: Error SQL al guardar la categoría del administrador

El parche MDVA-44940 corrige el problema en el que se produce un error SQL al guardar una categoría del administrador. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 está instalado. El ID del parche es MDVA-44940. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se produce un error de SQL al guardar una categoría del administrador.

<u>Pasos a seguir</u>:

1. Instalar datos de ejemplo.
1. Cree un segundo sitio web con un grupo de tienda asignado a la categoría predeterminada.

   * Crear una vista de tienda asignada al nuevo grupo de tiendas.

1. Crear stock y un origen adicional asignado a este stock y un canal de ventas asignado al segundo sitio web.
1. Cree un producto de prueba asignado al segundo sitio web.
1. Ir a **Administrador** > **Catálogo** > **Categorías**, seleccione **Ámbito** = **Segundo sitio web** y vaya a **Productos en la categoría** > **Ordenación automática** > Mueva los productos agotados al final y haga clic en **Guardar**.

<u>Resultados esperados</u>:

Se guardará la categoría.

<u>Resultados reales</u>:

Se produce el siguiente error: *Error al guardar la categoría*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
