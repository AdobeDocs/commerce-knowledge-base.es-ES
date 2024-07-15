---
title: "MDVA-33992: El precio personalizado B2B para el mayorista no se muestra en el carro de compras"
description: El parche MDVA-33992 soluciona el problema de que los precios personalizados para un cliente B2B no se reflejan cuando se añade un producto al carro de compras. Este parche está disponible cuando está instalada la herramienta Parches de calidad (QPT) 1.0.15. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.
exl-id: 6018fae6-762c-46c6-9497-ecf090115b7f
feature: B2B, Catalog Management, Orders, Shopping Cart
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-33992: El precio personalizado B2B para el mayorista no se muestra en el carro de compras

El parche MDVA-33992 soluciona el problema de que los precios personalizados para un cliente B2B no se reflejan cuando se añade un producto al carro de compras. Este parche está disponible cuando está instalada la herramienta Parches de calidad (QPT) 1.0.15. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:** Adobe Commerce en la infraestructura en la nube 2.4.1 con B2B

**Compatible con versiones de Adobe Commerce:** Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.0-2.4.1-p1 con B2B

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los precios personalizados para un cliente B2B no se reflejan cuando se agrega un producto al carro de compras.

<u>Pasos a seguir</u>:

El problema es reproducible para la versión B2B con el catálogo compartido habilitado.

1. Cree una empresa B2B con un catálogo compartido personalizado asignado.
1. Cree un producto en el catálogo personalizado de la empresa con un precio personalizado (precio de nivel).
1. Como cliente B2B, compruebe que el precio del producto personalizado se muestre en el catálogo.
1. Como cliente B2B, añada el producto al carro de compras.

<u>Resultado esperado</u>:

El precio correcto se muestra en el carro de compras y coincide con el precio del catálogo.

<u>Resultado real</u>:

El precio personalizado desaparece y se muestra el precio normal del catálogo predeterminado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos, según el producto de Adobe Commerce:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en la herramienta QPT, consulte la sección [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
