---
title: "MDVA-44703: Los totales de pedidos en el informe Pedidos se calculan incorrectamente"
description: El parche MDVA-44703 corrige el problema en el que los totales de pedidos del informe Pedidos se calculan de forma incorrecta para el usuario administrador restringido. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16. El ID del parche es MDVA-44703. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.
exl-id: d8c31e47-ace6-4dba-a57c-941e722a6aad
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# MDVA-44703: Los totales de pedidos en el informe Pedidos se calculan de forma incorrecta

El parche MDVA-44703 corrige el problema en el que los totales de pedidos del informe Pedidos se calculan de forma incorrecta para el usuario administrador restringido. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 está instalado. El ID del parche es MDVA-44703. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los totales de pedidos del informe Pedidos se calculan de forma incorrecta para el usuario administrador restringido.

<u>Pasos a seguir</u>:

1. Cree un sitio web adicional con dos tiendas.
1. Cree un usuario administrador restringido con acceso solo al nuevo sitio web.
1. Inicie sesión como usuario administrador restringido.
1. Cree dos pedidos con totales diferentes, uno para cada tienda nueva.
1. Cree facturas para los pedidos.
1. Ir a **Informes** > **Ventas** y abrir **Informe Pedidos**.
1. Actualizar estadísticas.
1. Consulte el informe de cada tienda.

<u>Resultados esperados</u>:

Los totales de ventas corresponden al importe del pedido de cada tienda.

<u>Resultados reales</u>:

Se muestra el total de ventas agregado de todo el sitio web de cada tienda.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
