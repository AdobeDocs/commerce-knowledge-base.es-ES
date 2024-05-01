---
title: "MDVA-37897: Redirección incorrecta al añadir productos de Vistos recientemente"
description: El parche MDVA-37897 resuelve el problema de la redirección incorrecta cuando los usuarios intentan agregar productos con opciones del widget de elementos visualizados recientemente. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1. El ID del parche es MDVA-37897. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.4 de Adobe Commerce.
exl-id: f0a86e02-b357-4d2d-8386-e9cc045bcf06
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-37897: redirección incorrecta al añadir productos de productos vistos recientemente

El parche MDVA-37897 resuelve el problema de la redirección incorrecta cuando los usuarios intentan agregar productos con opciones del widget de elementos visualizados recientemente. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 está instalado. El ID del parche es MDVA-37897. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.4 de Adobe Commerce.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce en nuestra infraestructura de nube 2.4.1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.2-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando un usuario intenta agregar un producto de la sección Vistos recientemente que tiene opciones requeridas para seleccionarse, se redirige al usuario a la página de lista de productos en lugar de a la página de detalles del producto.

<u>Pasos a seguir</u>:

1. Cree un producto sencillo con opciones personalizables (Tipo: Botón de opción).
1. Configure el widget de elementos visualizados recientemente para mostrar productos.
1. Visite los productos que tengan opciones personalizables para que aparezcan en el widget de elementos visualizados recientemente.
1. Clic **Añadir al carro** en uno de los productos del widget de elementos visualizados recientemente.

<u>Resultados esperados</u>:

Se le redirigirá a la página de detalles del producto para elegir las opciones.

<u>Resultados reales</u>:

Se le redirigirá a la página de lista de productos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos en función del tipo de implementación:

* Adobe Commerce on-premise: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en nuestra infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre parches de calidad para Adobe Commerce, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
