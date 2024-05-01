---
title: "Parche MDVA-31519: pérdida de pedido después del cierre de compra de los invitados"
description: El parche MDVA-31519 resuelve el problema en el que faltan pedidos pagados y bloquea los tiempos de espera en el cierre de compra de invitados.
exl-id: 2b4f9992-d58d-434f-adf8-d8ad8f761755
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Parche MDVA-31519: pérdida de pedido después del cierre de compra para invitados

El parche MDVA-31519 resuelve el problema en el que faltan pedidos pagados y bloquea los tiempos de espera en el cierre de compra de invitados.

Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14 está instalado. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.5-p2

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.5 - 2.3.5-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir</u>:

1. Habilitar cierre de compra de invitado.
1. Crear una regla de precio de carro de compras sin cupón (Ejemplo: &quot;Envío gratuito por encima de x cantidad&quot;).
1. Realice una gran cantidad de pedidos de invitado simultáneos que impliquen proveedores de servicios de pago de pagos (PSP) de API.

<u>Resultados esperados</u>:

Todas las transacciones de pago se guardan en la base de datos y se pueden ver en el Administrador, según lo esperado.

<u>Resultados reales</u>:

Solo una pequeña fracción de los pedidos se guarda en la base de datos, mientras que la mayoría de la información de los pedidos se pierde debido a los tiempos de espera de bloqueo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
