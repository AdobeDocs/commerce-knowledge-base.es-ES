---
title: "MDVA-36138: regla de envío gratuito no aplicada al carro de compras de varios artículos"
description: El parche de MDVA-36138 soluciona el problema de que, cuando hay varios artículos en el carro de compras, el SKU coincidente del envío gratuito no recibe el envío gratuito aplicado. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21. El ID del parche es MDVA-36138. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.
exl-id: 74e25ca8-e4fa-47f4-ab95-561f70e05727
feature: Orders, Shipping/Delivery, Personalization, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-36138: regla de envío gratuito no aplicada al carro de compras de varios artículos

El parche de MDVA-36138 soluciona el problema de que, cuando hay varios artículos en el carro de compras, el SKU coincidente del envío gratuito no recibe el envío gratuito aplicado. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 está instalado. El ID del parche es MDVA-36138. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.4

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.2 y superior

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Si una regla de envío gratuito se aplica solo a artículos específicos, el descuento no se aplica cuando hay otros artículos en el carro de compras.

<u>Pasos a seguir</u>:

1. Cree productos simples: simple1 y simple2.
1. Configure USPS (o cualquier método de envío en línea):

   * Métodos permitidos: correo con prioridad (un método seleccionado para no tener una larga lista de métodos en el carro de compras y el cierre de compra).
   * Método Libre: Correo Prioritario.

1. Crear una regla del carro de compras:

   * Especificar código de cupón
   * Pestaña Condiciones: dejar vacío
   * Pestaña Acciones:

   `Condition: SKU is simple1`
   `Free Shipping: For matching items only`

1. Agregue simple1 al carro de compras.
1. Aplique el código de cupón.
1. Agregue simple2 al carro de compras.

<u>Resultados esperados</u>:

* simple1 - debe tener envío gratuito.
* simple2: el envío debe pagarse.

<u>Resultados reales</u>:

El precio de envío incluye simple1 y simple2.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
