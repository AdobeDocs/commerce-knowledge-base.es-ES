---
title: "Parche MDVA-33559: error de pago rechazado de PayflowPro"
description: El parche MDVA-33559 resuelve el problema en el que se rechazan los pagos de PayPal PayflowPro.
exl-id: aec57ffa-07c7-404e-985d-8ec4fdb019b1
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Parche MDVA-33559: error de pago rechazado de PayflowPro

El parche MDVA-33559 resuelve el problema en el que se rechazan los pagos de PayPal PayflowPro.

Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:** Adobe Commerce en la infraestructura en la nube 2.3.5-p2

**Compatible con versiones de Adobe Commerce:** Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.0 - 2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El problema se refiere a los caracteres especiales del signo ampersand (&amp;) y del signo igual (=) que se utilizan en los nombres.

<u>Pasos a seguir</u>:

1. Añadir un producto simple al carro de compras.
1. Vaya a Pago y envío.
1. Establecer la dirección de envío. (Ejemplo de dirección de envío: **Nombre** = ** *John&#39;s* ** **Apellido** = ** *Apples &amp; Orange, Inc* ** **Dirección de la calle** = *1234 E Sin nombre St* **País** = *US* **Estado/Provincia** = *Cualquier estado* **Ciudad** *Cualquier pueblo* **Código postal** = *12345* **Teléfono** = *1234567890*)
1. Establece el pago en **PayPal PayflowPro** e intenta completar el pago y envío.

<u>Resultados esperados</u>:

La transacción genera un pago correcto o un mensaje de error correcto, según lo esperado.

<u>Resultados reales</u>:

La transacción se rechaza y el cliente recibe un correo electrónico que dice: &quot;Se ha rechazado la transacción&quot;.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos, según el producto de Adobe Commerce:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en la herramienta QPT, consulte la sección [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
