---
title: "Parche de MDVA-31363: No se aplica la regla de precio del carro de compras (GraphQL)"
description: El parche MDVA-31363 corrige el problema en el que la regla de precio del carro de compras con cupón no se aplica a través de GraphQL cuando se utiliza la acción "Descuento de cantidad fija para el carro de compras completo". Este parche está disponible cuando está instalada la herramienta Parches de calidad (QPT) 1.0.9. Está previsto que el problema se corrija en la versión 2.4.2 de Adobe Commerce.
exl-id: f64fbbb1-b5fd-4624-bcdd-d1e6c1f9acfe
feature: GraphQL, Orders, Price Rules, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Parche MDVA-31363: No se aplica la regla de precio del carro de compras (GraphQL)

>[!WARNING]
>
>Un nuevo parche llamado MDVA-33975 soluciona los problemas de cálculo de precios de GraphQL. MDVA-31363 está depreciado y se recomienda aplicar el parche MDVA-33975. Para acceder a este parche, consulte [Parche MDVA-33975: cálculos de precios de GraphQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html).

El parche MDVA-31363 corrige el problema en el que la regla de precio del carro de compras con cupón no se aplica a través de GraphQL cuando se utiliza la acción &quot;Descuento de cantidad fija para el carro de compras completo&quot;. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9. Está previsto que el problema se corrija en la versión 2.4.2 de Adobe Commerce.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.4.0

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.2 - 2.4.1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Volver a calcular los totales de las cotizaciones antes de responder sobre los precios provoca que se pierdan las reglas aplicadas.

<u>Pasos a seguir</u>:

1. Cree un producto sencillo.
1. Cree una regla de precio de carro de compras con un descuento de cantidad fija para todo el carro de compras.
1. Cree un nuevo carro de compras con GraphQL.
1. Guarde la tarjeta\_id de la respuesta y añada el producto del paso 1 al carro de compras mediante GraphQL.
1. Activar la regla de precio del carro de compras añadiendo el código de cupón al carro de compras mediante GraphQL.
1. Consultar precio en respuesta.

<u>Resultados esperados</u>:

Se aplica un descuento.

<u>Resultados reales</u>:

El descuento no se aplica.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
