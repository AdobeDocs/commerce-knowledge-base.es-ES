---
title: '"MDVA-42520: Tipo impositivo aplicado dos veces cuando se utiliza "Habilitar comercio transfronterizo"'
description: El parche de MDVA-42520 corrige el problema en el que la tasa impositiva se aplica dos veces cuando se utiliza el **Enable Cross Border Trade**. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11. El ID del parche es MDVA-42520. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: c1ca44eb-fe92-4f28-807a-3a4563433386
feature: Catalog Management, Orders, Taxes
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# MDVA-42520: tipo impositivo aplicado dos veces cuando se utiliza &quot;Habilitar comercio transfronterizo&quot;

El parche MDVA-42520 corrige el problema en el que la tasa impositiva se aplica dos veces cuando se utiliza **Habilitar comercio internacional**. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11. El ID del parche es MDVA-42520. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La tasa de impuestos se aplica dos veces cuando se usa **Habilitar comercio transfronterizo**.

<u>Pasos a seguir</u>:

1. Habilitar **Compañía**, **Catálogo compartido** y **Presupuesto**
1. Configure los impuestos según la captura de pantalla. Asegúrese de habilitar **comercio transfronterizo**.

   ![configuración de impuestos](/help/support-tools/patches-available-in-qpt-tool/assets/tax_settings_1.png){width="700"}

1. Cree un tipo impositivo para Alemania (10 %).
1. Cree una regla fiscal para aplicar el tipo impositivo.
1. Cree una empresa y un catálogo compartido personalizado.
1. Cree un producto con un precio de 100 e inclúyalo en el catálogo compartido personalizado con un descuento del 20 % en el precio.
1. Cree un cliente con una dirección en alemán y asígnelo a la compañía
1. Agregue 10 productos a la tarjeta como cliente.
1. Vaya al carro de compras y solicite un presupuesto.
1. Abra este presupuesto en el backend de e intente añadir un descuento adicional del 10%.

<u>Resultados esperados</u>:

Subtotal de Oferta (Impuestos Incluidos) y Total General de Oferta (Impuestos Incluidos) = 720 $

<u>Resultados reales</u>:

Subtotal de la oferta (impuestos incluidos) y Total general de la oferta (impuestos incluidos) = 649,50 $.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/usage) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en nuestra documentación para desarrolladores.
