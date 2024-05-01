---
title: "MDVA-35197: Error de adición al carro de compras de GraphQL si se añaden productos sin existencias"
description: El parche MDVA-35197 corrige el problema en el que se produce un error al añadir al carro de compras con GraphQL si los productos añadidos anteriormente no están disponibles. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17.
exl-id: 189312f7-a505-4ba4-b12d-662987e69374
feature: GraphQL, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-35197: error de adición al carro de compras de GraphQL si se añaden productos sin existencias

El parche MDVA-35197 corrige el problema en el que se produce un error al añadir al carro de compras con GraphQL si los productos añadidos anteriormente no están disponibles. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 está instalado.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.6

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.5 - 2.3.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Error al intentar añadir un producto al carro de compras mediante GraphQL si el otro producto que ya está en el carro (también añadido mediante GraphQL) está agotado.

<u>Pasos a seguir</u>:

1. Con GraphQL, añada cualquier producto al carro de compras.
1. Inicie sesión en el panel de administración de Commerce y configure este producto como agotado.
1. Intente añadir otro producto al carro de compras mediante GraphQL.

<u>Resultados esperados</u>:

Los productos en existencia se pueden añadir al carro de compras.

<u>Resultados reales</u>:

Mensaje de error de GraphQL: *Algunos de los productos están agotados*. No se puede añadir un nuevo producto &quot;en stock&quot;.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
