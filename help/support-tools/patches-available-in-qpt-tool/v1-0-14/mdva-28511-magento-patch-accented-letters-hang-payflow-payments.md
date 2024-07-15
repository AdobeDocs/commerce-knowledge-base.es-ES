---
title: "MDVA-28511: las cartas acentuadas cuelgan los pagos de flujo de pago"
description: El parche de MDVA-28511 resuelve el problema cuando los pagos a través de **Payflow Pro** no se completan para los nombres de clientes con letras acentuadas.
exl-id: ecc827e3-2a1c-4f32-a0e2-9c5792483e7d
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MDVA-28511: las cartas acentuadas cuelgan los pagos de flujo de pago

El parche de MDVA-28511 resuelve el problema cuando los pagos a través de **Payflow Pro** no se completan para los nombres de clientes con letras acentuadas.

Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14. Tenga en cuenta que el problema se corrigió en la versión 2.3.6 de Adobe Commerce.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:** Adobe Commerce en la infraestructura en la nube 2.3.5-p1

**Compatible con versiones de Adobe Commerce:** Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.5 - 2.3.5-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Requisito previo</u>:

Habilitar el método de pago con tarjeta de crédito **Payflow Pro**.

<u>Pasos a seguir</u>:

1. Añada un producto al carro de compras y continúe con la página de cierre de compra.
1. Establecer un nombre de cliente con letras acentuadas. (Ejemplo: **Ãtienne Ãillin**)
1. Continúe con los pasos de pago.
1. Seleccione **Payflow Pro** como **Tarjeta de crédito** y rellene los detalles de la tarjeta de crédito.
1. Haga clic en el botón **Realizar pedido**.

<u>Resultados esperados</u>:

El pedido se completa sin ningún problema, según lo esperado.

<u>Resultados reales</u>:

El pedido no se completa y los registros mostrarán un error similar al de este ejemplo:

```php
[2020-06-12 07:50:23] report.CRITICAL: String to be escaped was not valid UTF-8 or could not be converted: �?tienne �?illini [] []
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
