---
title: "MDVA-44100: todos los FTP se asignan al último producto del carro de compras"
description: El parche MDVA-44100 resuelve el problema de asignación de todos los FTP al último producto del carro de compras. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14. El ID del parche es MDVA-44100. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: ab0f195c-fcc6-41ac-932d-d2603d068aa6
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-44100: todos los FTP se asignan al último producto del carro de compras

El parche MDVA-44100 resuelve el problema de asignación de todos los FTP al último producto del carro de compras. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 está instalado. El ID del parche es MDVA-44100. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Todos los FTP se asignan al último producto del carro de compras y se restablecen los valores FTP del resto de los productos.

<u>Pasos a seguir</u>:

1. Ir a **Tiendas** > **Configuración** > **Ventas** > **Impuestos** y establezca:
   * Activar FTP = Sí
   * Aplicar Impuesto a FTP = Sí
   * Incluir FTP en el subtotal = Sí
1. Ir a **Tiendas** > **Atributo** > **Product** y cree un nuevo atributo con type = Impuesto de producto fijo.
1. Agregue el atributo a un conjunto de atributos.
1. Cree dos productos a partir del conjunto de atributos y configure el atributo FTP para su país y estado.
1. Añada ambos elementos al pedido.
1. Escriba una dirección que requiera que se pague el FTP.
1. Realice el pedido.
1. Compruebe la lista de artículos en el pedido.

<u>Resultados esperados</u>:

Los FTP se muestran debajo de cada producto.

<u>Resultados reales</u>:

Los valores de FTP de ambos elementos se muestran debajo del segundo elemento.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
