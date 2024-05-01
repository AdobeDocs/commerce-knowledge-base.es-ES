---
title: "MDVA-39923: la búsqueda por SKU en la funcionalidad de pedido rápido B2B distingue entre mayúsculas y minúsculas"
description: El parche de MDVA-39923 soluciona el problema en el que los clientes obtienen un error cuando buscan el pedido por SKU en la funcionalidad de pedido rápido B2B con un caso diferente al del caso con el que se guarda el nombre. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. El ID del parche es MDVA-39923. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: 52e435df-28a7-49be-a257-7e5801601d57
feature: B2B, Catalog Management, Orders, Search
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-39923: la búsqueda por SKU en la funcionalidad de pedido rápido B2B distingue entre mayúsculas y minúsculas

El parche de MDVA-39923 soluciona el problema en el que los clientes obtienen un error cuando buscan el pedido por SKU en la funcionalidad de pedido rápido B2B con un caso diferente al del caso con el que se guarda el nombre. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 está instalado. El ID del parche es MDVA-39923. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.1-p1

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La búsqueda por SKU en la funcionalidad de pedido rápido B2B distingue entre mayúsculas y minúsculas y muestra un error cuando se utiliza un caso diferente al con el que se guarda el SKU.

<u>Requisitos previos</u>:

Los módulos B2B están instalados.

<u>Pasos a seguir</u>:

1. Inicie sesión en el administrador de y vaya a **Tiendas** > **Configuración** > **B2B**.
1. Activar **Catálogo compartido** y **Pedido rápido**.
1. Cree un producto con SKU en mayúsculas, por ejemplo, TEST20-1234
1. Asignar el producto creado a **Catálogo compartido**.
1. Inicie sesión como cliente y haga clic en **Pedido rápido**.
1. Introduzca el SKU en minúsculas; por ejemplo, test20-1234.

<u>Resultados esperados</u>:

El producto debe encontrarse independientemente de la caja utilizada.

<u>Resultados reales</u>:

Se recibe el siguiente mensaje de error: *1 producto(s) requiere(n) su atención*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
