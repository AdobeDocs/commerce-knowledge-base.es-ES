---
title: ¿Puedo programar actualizaciones de Ensayo de contenido para precios en un catálogo compartido?
description: Adobe Commerce no ofrece la funcionalidad de programar una actualización de precios ([Ensayo de contenido](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html)) para uno o varios productos en un catálogo compartido.
exl-id: 5482326f-54c2-4efc-8e5e-6d075ee5be55
feature: Catalog Management, Customer Service
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# ¿Puedo programar actualizaciones de Ensayo de contenido para precios en un catálogo compartido?

Adobe Commerce no ofrece la funcionalidad de programar una actualización de precios ([Ensayo de contenido](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html)) para uno o varios productos de un catálogo compartido.

Eso significa que no puedes programar una actualización de precios directamente desde el menú **Establecer precios y estructura** del panel de administración de Commerce (no hay ningún botón **Programar nueva actualización** en este menú).

Sin embargo, puede utilizar métodos alternativos y programar una actualización de precios para:

* un grupo de clientes
* el precio base del producto

## Programar actualización de precios para un grupo de clientes

1. Iniciar [programación de una nueva actualización de producto](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html).
1. Desplácese hacia abajo hasta el campo **Precio** y haga clic en **Precios avanzados**.

   ![advanced_price.png](assets/advanced_pricing.png){width="600"}

1. En la sección **Precio de grupo de clientes**, seleccione el grupo de clientes necesario y establezca el precio actualizado.

   ![customer_group_price.png](assets/customer_group_price.png){width="700"}

1. Termine de programar la actualización como de costumbre.

En este flujo de trabajo, solo puede actualizar el precio de un único producto; la actualización de precios globales no está disponible.

Recuerde: los catálogos compartidos aprovechan los precios del grupo de clientes.

**Documentación relacionada**

* [Programando una actualización (Ensayo de contenido)](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html) en nuestra guía del usuario.
* [Precios avanzados](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html) en nuestra guía del usuario.

## Programar actualización de precios para el precio base

Consulte el artículo relacionado: [¿Cómo afecta el cambio del precio base al precio del catálogo compartido?](/help/faq/general/base-price-change-affect-on-shared-catalog-price.md) en nuestra base de conocimiento de soporte.
