---
title: "MDVA-30972: envío incorrecto del estado del pedido creado mediante la API de REST"
description: El parche MDVA-30972 soluciona el problema de que el estado del pedido se cambia incorrectamente durante la creación del envío mediante la API de REST. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7.
exl-id: 70b8db1f-16d0-48f4-b0a2-483a7176cb89
feature: REST, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# MDVA-30972: envío incorrecto del estado del pedido creado mediante la API de REST

El parche MDVA-30972 soluciona el problema de que el estado del pedido se cambia incorrectamente durante la creación del envío mediante la API de REST. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalado.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce en infraestructura en la nube 2.3.5-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 a 2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando se crea un envío parcial desde el administrador mediante la API de REST para un pedido con *Sospecha de fraude* estado del pedido, el estado del pedido se cambia a *Procesando*. Debe permanecer en *Sospecha de fraude*.

<u>Requisitos previos</u>:

* Se ha configurado PayPal EC u otra forma de pago en línea.
* La integración para la API de REST está configurada.

<u>Pasos a seguir</u>:

1. Cree un pedido con dos o más elementos.
1. Iniciar sesión en **Administrador** > **Ventas** > **Pedidos**. Abra el pedido que acaba de crear.
1. En la página de detalles del pedido, desplácese hacia abajo hasta **Total de pedido**. Haga clic en **Estado** y seleccione. *Sospecha de fraude*. Luego haga clic en **Enviar comentario** botón.
1. Compruebe que el pedido tenga *Sospecha de fraude* estado ahora.
1. Cree un envío para un artículo a partir del pedido mediante la API de REST:

   ```
   * Method = `Post`
   * Header = `"{host}/rest/V1/orders/ {order_id}/ship"`
   * Body =
   ```

   ```
    {      "items": [        {          "extension_attributes": {},          "order_item_id": {order_item_id},          "qty": 1        }      ]    }
   ```

1. Vuelva a abrir el pedido en Administración y compruebe su estado.

<u>Resultados esperados</u>:

* Estado del pedido = *Sospecha de fraude*.
* El estado del pedido no cambia si se crea el mismo envío desde el administrador.

<u>Resultados reales</u>:

Estado del pedido = *Procesando*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
