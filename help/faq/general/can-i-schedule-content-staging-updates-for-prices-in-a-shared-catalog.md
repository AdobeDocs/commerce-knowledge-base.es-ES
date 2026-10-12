---
title: ¿Puedo programar actualizaciones de Ensayo de contenido para precios en un catálogo compartido?
description: Adobe Commerce no ofrece la funcionalidad de programar una actualización de precios ([Ensayo de contenido](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html?lang=es)) para uno o varios productos en un catálogo compartido.
exl-id: 5482326f-54c2-4efc-8e5e-6d075ee5be55
feature: Catalog Management, Customer Service
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
subfeature_v2:
  - id: deedbb4d-f1b7-58ea-a34a-de1f481f9d4c
    internal-label: Customer Service
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%
---
# ¿Puedo programar actualizaciones de Ensayo de contenido para precios en un catálogo compartido?

Adobe Commerce no ofrece la funcionalidad de programar una actualización de precios ([Ensayo de contenido](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html?lang=es)) para uno o más productos de un catálogo compartido.

Eso significa que no puedes programar una actualización de precios directamente desde el menú **Establecer precios y estructura** del panel de administración de Commerce (no hay ningún botón **Programar nueva actualización** en este menú).

Sin embargo, puede utilizar métodos alternativos y programar una actualización de precios para:

* un grupo de clientes
* el precio base del producto

## Programar actualización de precios para un grupo de clientes

1. Iniciar [programación de una nueva actualización de producto](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html?lang=es).
1. Desplácese hacia abajo hasta el campo **Precio** y haga clic en **Precios avanzados**.

   ![advanced_price.png](assets/advanced_pricing.png){width="600"}

1. En la sección **Precio de grupo de clientes**, seleccione el grupo de clientes necesario y establezca el precio actualizado.

   ![customer_group_price.png](assets/customer_group_price.png){width="700"}

1. Termine de programar la actualización como de costumbre.

En este flujo de trabajo, solo puede actualizar el precio de un único producto; la actualización de precios globales no está disponible.

Recuerde: los catálogos compartidos aprovechan los precios del grupo de clientes.

**Documentación relacionada**

* [Programando una actualización (Ensayo de contenido)](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html?lang=es) en nuestra guía del usuario.
* [Precios avanzados](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html?lang=es) en nuestra guía del usuario.

## Programar actualización de precios para el precio base

Vea el artículo relacionado: [¿Cómo afecta el cambio de precio base al precio de catálogo compartido?](/help/faq/general/base-price-change-affect-on-shared-catalog-price.md) en nuestra base de conocimiento de soporte.
