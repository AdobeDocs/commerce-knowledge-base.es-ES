---
title: "ACSD-43887: Detalles incorrectos mostrados en la página de pago de cierre de compra"
description: El parche ACSD-43887 corrige el problema en el que se muestran detalles incorrectos en la página de pago de cierre de compra cuando se activan los pedidos de compra para empresas. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17. El ID del parche es ACSD-43887. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.
exl-id: 07b17f96-5236-43a7-aeaf-6bfe36c551cf
feature: B2B, Checkout, Orders, Payments, User Account
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 0%

---

# ACSD-43887: detalles incorrectos mostrados en la página de pago del cierre de compra

El parche ACSD-43887 corrige el problema en el que se muestran detalles incorrectos en la página de pago de cierre de compra cuando se activan los pedidos de compra para empresas. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 está instalado. El ID del parche es ACSD-43887. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los detalles incorrectos se muestran en la página de pago de cierre de compra cuando se habilitan los pedidos de compra para empresas.

<u>Requisitos previos</u>:

1. Los módulos B2B están instalados.
1. Habilitar la compañía se establece en _Sí_. Ir a **Tiendas** > **Configuraciones** > **General** > **Funciones B2B** > **Habilitar compañía** > **Sí**.
1. Habilitar pedidos de compra está establecido en _Sí_. Ir a **Configuración de aprobación de pedidos** > **Activar pedidos de compra** > **Sí**.
1. PayPal Express está configurado como forma de pago.

<u>Pasos a seguir</u>:

1. Cree un producto virtual.
1. Registre una cuenta de empresa desde el front-end con un administrador de empresa.
1. Aprobar la cuenta de empresa desde el backend y establecer **Activar pedidos de compra** as _Sí_ al aprobar la empresa.
1. Vaya al front-end e inicie sesión con la cuenta de administrador de la empresa creada en el paso dos.
1. Cree un &quot;Usuario predeterminado&quot; para la empresa. Ir a **Usuario de empresa** > **Añadir nuevo usuario**.
1. Cree una &quot;regla de aprobación&quot; para la empresa. Ir a **Reglas de aprobación** > **Añadir nueva regla**.

   * Tipo de regla: Total de pedido
   * Total de pedido: es superior o igual a 1 $
   * Requiere aprobación de: Administrador de la empresa

1. Cierre la sesión e inicie sesión con la cuenta &quot;Usuario predeterminado&quot;.
1. Añada el producto virtual creado en el paso uno al carro de compras y continúe con el cierre de compra.
1. Selecciona PayPal Express como forma de pago y haz clic en **Realizar pedido de compra**.
1. Cierre la sesión e inicie sesión con la cuenta de administrador de la empresa.
1. Ir a **Mis pedidos de compra** y desde **Pedidos de compra de empresa**, haga clic en **Ver** para el pedido creado en el paso nueve.
1. Apruebe el pedido de compra. El estado del pedido de compra debe ser &quot;Aprobado: Pago pendiente&quot;.
1. Cierre la sesión y vuelva a iniciarla con la cuenta &quot;Usuario predeterminado&quot; de la empresa.
1. Ir a **Mis pedidos de compra** > **Ver** > **Realizar pedido**.
1. Compruebe la **Resumen de pedidos**.

<u>Resultados esperados</u>:

El resumen del pedido muestra valores correctos distintos de cero.

<u>Resultados reales</u>:

El valor total de resumen del pedido es cero.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
