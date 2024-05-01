---
title: "MDVA-42645: El administrador no puede devolver puntos de recompensa por el crédito de tienda deshabilitado"
description: El parche MDVA-42645 resuelve el problema en el que el administrador no puede devolver puntos de recompensa si la funcionalidad de crédito de la tienda está desactivada. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. El ID del parche es MDVA-42645. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: 8e8f8c07-c1a2-4031-a2fb-cb737165dc2c
feature: Admin Workspace, Orders, Rewards, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-42645: El administrador no puede devolver puntos de recompensa por el crédito de tienda deshabilitado

El parche MDVA-42645 resuelve el problema en el que el administrador no puede devolver puntos de recompensa si la funcionalidad de crédito de la tienda está desactivada. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 está instalado. El ID del parche es MDVA-42645. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El administrador no puede reembolsar puntos de recompensa si la funcionalidad de crédito de la tienda está desactivada.

<u>Pasos a seguir</u>:

1. Cree un producto sencillo.
1. Cree una nueva cuenta de cliente y añada algunos puntos de recompensa.
1. Desactive la funcionalidad de crédito de tienda accediendo a **Almacenar** > Configuración > **Configuración** > **Cliente** > **Configuración del cliente** > **Opciones de crédito de tienda**.
1. Inicie sesión como el cliente al que se asignan los puntos de recompensa.
1. Añada un producto al carro de compras y navegue hasta el cierre de compra.
1. Utilice los puntos de recompensa en la sección de pago y realice el pedido.
1. Abra el pedido en el administrador y factura el pedido.
1. Haga clic en **Nota de crédito** para crear un nuevo abono.
1. Marque la opción Reembolsar puntos de recompensa en la parte inferior y haga clic en **Reembolso sin conexión**.

<u>Resultados esperados</u>:

* El abono se ha creado correctamente.
* Los puntos de recompensa se reembolsan correctamente.

<u>Resultados reales</u>:

Recibe el siguiente mensaje de error: *No puede usar más crédito de tienda que el importe del pedido.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
