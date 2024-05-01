---
title: "Parche MDVA-33976: paquete sin existencias después de eliminar la opción"
description: El parche MDVA-33976 corrige el problema en el que un producto agrupado aparece como Agotado después de que una de sus opciones se haya eliminado en Administración. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT) 1.0.15](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp). Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.
exl-id: 2e2bc05b-ad31-4e87-b33e-3526f6a42478
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# Parche de MDVA-33976: paquete sin existencias después de eliminar la opción

El parche MDVA-33976 corrige el problema en el que un producto agrupado aparece como Agotado después de que una de sus opciones se haya eliminado en Administración. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT) 1.0.15](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) está instalado. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:** Adobe Commerce en infraestructura en la nube 2.3.3

**Compatible con las versiones de Adobe Commerce:** Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.0-2.3.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir</u>:

1. Abra un paquete de productos en el Administrador de Commerce.
1. Elimine una de las opciones de producto del paquete.
1. Guardar cambios.
1. Abra el producto en la tienda.

<u>Resultado esperado</u>:

El estado de stock del producto del paquete se actualiza según el estado de stock del producto secundario.

<u>Resultado real</u>:

El producto agrupado se muestra como Agotado, independientemente del estado del producto secundario.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos, según el producto de Adobe Commerce:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en la herramienta QPT, consulte la [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
