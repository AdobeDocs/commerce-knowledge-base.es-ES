---
title: "MDVA-38270: Cantidad de la tarjeta de regalo que falta en el total del pedido del cliente"
description: El parche MDVA-38270 corrige el problema cuando la cantidad de la tarjeta regalo no se encuentra en el total del pedido del cliente. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25. El ID del parche es MDVA-38270. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.
exl-id: 4ab315c4-d26e-4270-a556-66601d01fb2e
feature: Gift, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# MDVA-38270: Cantidad de la tarjeta de regalo que falta en el total del pedido del cliente

El parche MDVA-38270 corrige el problema cuando la cantidad de la tarjeta regalo no se encuentra en el total del pedido del cliente. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 está instalado. El ID del parche es MDVA-38270. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**
Adobe Commerce en infraestructura en la nube 2.4.2-p1

**Compatible con las versiones de Adobe Commerce:**
Adobe Commerce (todos los métodos de implementación) 2.4.1-2.4.2-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Falta la cantidad de la tarjeta de regalo en la respuesta total del pedido.

<u>Requisitos previos</u>:

1. Cree una cuenta de cliente.
1. Realice un pedido con una tarjeta regalo (la tarjeta regalo cubre todo el pedido).

<u>Pasos a seguir</u>:

Realizar una consulta del cliente para el cliente, pedidos, artículos, total:

```GraphQL
query {
  customer {
    orders(
      pageSize: 20
    ) {
      items {
        id
        order_date
        total {
          grand_total {
            value
            currency
          }
          total_giftcard {
              applied_balance {
                value
                currency
              }
              code
              current_balance {
                value
                currency
              }
              expiration_date
          }
        }
        status
      }
    }
  }
}
```

<u>Resultados esperados</u>:

`total_giftcard` Este campo está disponible.

<u>Resultados reales</u>:

No hay campos relacionados con tarjetas regalo disponibles.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos en función del método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html).

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obtener más información sobre otros parches disponibles en la herramienta QPT, consulte la [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
