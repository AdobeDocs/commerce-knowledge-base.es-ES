---
title: "MDVA-40101: Los artículos permanecen en el minicarrito después de la colocación del pedido PayPal Express Checkout"
description: El parche de MDVA-40101 soluciona el problema de no eliminar artículos del minicarrito tras realizar correctamente un pedido con PayPal Express Checkout. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4. El ID del parche es MDVA-40101. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.0.
exl-id: d640dfcd-6fb6-4cc6-8817-3ae19aa59bed
feature: Checkout, Orders, Payments, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-40101: Los artículos permanecen en el minicarrito después de la realización del pedido

El parche de MDVA-40101 soluciona el problema de no eliminar artículos del minicarrito tras realizar correctamente un pedido con PayPal Express Checkout. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4. El ID del parche es MDVA-40101. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.0.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.7

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.2 - 2.3.7-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los artículos permanecen en el minicarrito incluso después de que se haya realizado correctamente un pedido mediante el Pago y envío de PayPal Express.

<u>Pasos a seguir</u>:

Realiza un pedido con PayPal Express Checkout en el modo Incognito en un navegador.

<u>Resultados esperados</u>:

El minicarrito debe estar vacío una vez completado correctamente el pedido.

<u>Resultados reales</u>:

* La página de éxito muestra un minicarrito vacío.
* Todas las demás páginas muestran minicarrito con artículos comprados.
* Al hacer clic en el vínculo del carro de compras, se le redirige a una página vacía del carro de compras.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/usage) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
