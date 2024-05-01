---
title: "MDVA-30565: problema de registro y almacenamiento local de caché de sesión"
description: El parche de MDVA-30565 soluciona el problema del almacenamiento local y el cierre de compra de la caché de sesión. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6.
exl-id: f0693f0c-fc6b-44af-a6a0-ebfa973bca65
feature: Cache, Checkout, Orders, Storage
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-30565: problema de registro y almacenamiento local de caché de sesión

El parche de MDVA-30565 soluciona el problema del almacenamiento local y el cierre de compra de la caché de sesión. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 está instalado.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce en infraestructura en la nube 2.3.3-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los artículos del carro de compras aún se pueden ver en la página del carro de compras cuando se agota el tiempo de espera de una sesión del cliente. Esto provoca un error de método de envío estimado en el que no hay métodos de envío disponibles para el cierre de compra de los invitados.

<u>Pasos a seguir</u>:

1. Habilite el carro de compras persistente en el administrador de Commerce. (**Habilitar persistencia** = &quot;*Sí*&quot;)
1. Inicie sesión como cliente en el front-end. Esto crea el `persistent_shopping_cart` e inicia una sesión persistente.
1. Añadir un producto al carro de compras.
1. Espere hasta que se agote el tiempo de espera de la sesión de front-end o elimine el `PHPSESSID` cookie.
1. Ahora es un usuario invitado, pero si va al carro de compras, aún puede ver el producto que se agregó como cliente registrado.
1. Eliminar el producto del carro de compras y ahora el carro de compras está vacío. Puede ver que Adobe Commerce elimina el `persistent_shopping_cart` cookie en este evento.
1. Añada un nuevo producto al carro de compras y vaya a la página del carro de compras.
1. Ahora, en la consola del explorador, se muestra `V1/guest-carts/4/estimate-shipping-methods` La solicitud ahora devuelve una respuesta 404 con un mensaje `{"message":"No such entity        with %fieldName = %fieldValue","parameters":{"fieldName":"cartId","fieldValue":0}}`

<u>Resultados esperados</u>:

La solicitud de método de envío de estimación devuelve los resultados correctos.

<u>Resultados reales</u>:

La solicitud del método de envío de estimación falla con un error como, &quot;*Lo sentimos, no hay presupuestos disponibles para este pedido en este momento.*&quot;

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
