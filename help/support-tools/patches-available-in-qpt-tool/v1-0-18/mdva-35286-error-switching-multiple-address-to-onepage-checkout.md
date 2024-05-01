---
title: "MDVA-35286: error al cambiar varias direcciones a una comprobación de página"
description: El parche MDVA-35286 corrige el problema en el que hay un error si un cliente tiene productos agrupados en el carro de compras y cambia de cierre de compra de varias direcciones a cierre de compra de una sola página. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18. El ID del parche es MDVA-35286. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.
exl-id: 40c98735-6054-4b25-9882-e274424b203f
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-35286: error al cambiar varias direcciones a una comprobación de página

El parche MDVA-35286 corrige el problema en el que hay un error si un cliente tiene productos agrupados en el carro de compras y cambia de cierre de compra de varias direcciones a cierre de compra de una sola página. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 está instalado. El ID del parche es MDVA-35286. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en la infraestructura en la nube 2.4.1

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.0-2.4.1-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se muestra un error si hay un producto agrupado en el carro de compras y el usuario intenta utilizar el cierre de compra de una página después de abandonar el cierre de compra de envío múltiple.

<u>Pasos a seguir</u>:

1. Inicie sesión en la cuenta de cliente de y agregue más de un paquete de productos al carro de compras.
1. Haga clic en el vínculo para ver y editar el carro de compras.
1. Haga clic en **Desproteger con varias direcciones** vínculo.
1. Seleccione direcciones diferentes para los productos agregados al carro de compras.
1. Clic **Volver al carro de compras**.
1. En el carro, haga clic en **Continuar con el cierre**.

<u>Resultados esperados</u>:

Se le redirigirá a la página Cierre de compra.

<u>Resultados reales</u>:

Se muestra el siguiente mensaje de error: *Se ha producido un error al procesar su solicitud*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
