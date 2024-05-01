---
title: "MDVA-32545 patch: las facturas de pedidos no se envían automáticamente"
description: El parche MDVA-32545 corrige el problema en el que los correos electrónicos de factura no se envían automáticamente al cliente para los pedidos realizados desde el administrador. Esto afecta a cualquier forma de pago con el tipo de transacción **Venta**, como **Braintree ** o **PayPal Payflow Pro**.
exl-id: 682eaeb1-5475-4d37-9536-0605f5b9f163
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Parche MDVA-32545: las facturas de pedidos no se envían automáticamente

El parche MDVA-32545 corrige el problema en el que los correos electrónicos de factura no se envían automáticamente al cliente para los pedidos realizados desde el administrador. Esto afecta a cualquier método de pago con **Venta** tipo de transacción, como **Braintree** o **PayPal Payflow Pro**.

Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 está instalado. Tenga en cuenta que el problema se corrigió en la versión 2.4.2 de Adobe Commerce.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.2-p2

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.0 - 2.4.1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir</u>:

1. Habilite cualquier forma de pago con **Venta** tipo de transacción. (Por ejemplo: **Braintree** o **PayPal Payflow Pro**.)
1. Cree un producto sencillo.
1. Cree una cuenta de cliente en el front-end.
1. Realice un pedido desde el administrador.

<u>Resultados esperados</u>:

El correo electrónico de factura se envía al cliente automáticamente, según lo esperado.

<u>Resultados reales</u>:

El correo electrónico de factura no se envía al cliente automáticamente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
