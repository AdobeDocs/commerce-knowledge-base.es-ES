---
title: "ACSD-48910: El producto agrupado asignado a varias fuentes se queda sin existencias después de la factura y el envío"
description: Aplique el parche ACSD-48910 para solucionar el problema de Adobe Commerce en el que el producto agrupado asignado a varios orígenes se queda sin existencias después de facturar y enviar un pedido, incluso si sigue teniendo una cantidad distinta de cero.
feature: Products, Inventory
role: Admin, Developer
exl-id: 6ac3dedf-1c28-4874-b963-44a429b37983
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-48910: el producto agrupado asignado a varias fuentes se queda sin existencias después de la factura y el envío

El parche ACSD-48910 soluciona el problema de que el producto agrupado asignado a varios orígenes se queda sin existencias después de que se factura y envía un pedido, incluso si aún tiene una cantidad distinta de cero. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42. El ID del parche es ACSD-48910. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El producto agrupado asignado a varios orígenes se queda sin existencias después de la facturación y el envío, incluso si aún está disponible.

<u>Pasos a seguir</u>:

1. Cree dos sitios web.
1. Cree dos tiendas o vistas de tiendas (una por sitio web).
1. Cree dos productos simples (cantidad = 10) y asígnelos tanto a stock como a sitios web.
1. Cree un producto agrupado y añádale estos productos simples. Asigne el producto agrupado a ambos sitios web.
1. Vaya a la tienda y añada el producto agrupado al carro de compras.
1. Eche un vistazo y haga el pedido.
1. Desde el administrador, factura y envía el pedido.

<u>Resultados esperados</u>:

El producto en paquete permanece en stock ya que solo compramos 1 de los 10 artículos.

<u>Resultados reales</u>:

El producto agrupado cambia su estado a agotado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
