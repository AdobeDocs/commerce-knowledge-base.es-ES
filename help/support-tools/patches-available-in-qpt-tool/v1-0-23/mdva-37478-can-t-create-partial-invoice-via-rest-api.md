---
title: "MDVA-37478: No se puede crear una factura parcial mediante la API de REST"
description: El parche MDVA-37478 soluciona el problema cuando no puedes crear una factura parcial a través de la API REST para un pedido realizado con el método de pago **Pago a cuenta**. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23. El ID del parche es MDVA-37478. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.3 de Adobe Commerce.
exl-id: 1b235baa-a188-467c-8ae5-de0836bc2caa
feature: REST, B2B, Invoices
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-37478: No se puede crear una factura parcial mediante la API de REST

El parche MDVA-37478 soluciona el problema cuando no puedes crear una factura parcial a través de la API REST para un pedido realizado con una forma de pago **Pago a cuenta**. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 está instalado. El ID del parche es MDVA-37478. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

* El parche se ha diseñado para Adobe Commerce en la infraestructura en la nube 2.3.3-p1
* El parche también es compatible con Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.0-2.3.7

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Requisito previo</u>:

Adobe Commerce con módulo B2B instalado

<u>Pasos a seguir</u>:

1. Activar **Empresa B2B**.
1. Activar **Pago a cuenta** forma de pago.
1. Cree 2 productos sencillos.
1. Cree una cuenta de compañía.
1. Agregue créditos de la compañía que excedan el precio total de 2 productos creados.
1. Inicie sesión en el front-end mediante la cuenta de compañía creada.
1. Añada los 2 productos creados al carro de compras y cierre de compra con el **Pago a cuenta** forma de pago.
1. Intente crear una factura parcial para el pedido creado mediante la API de REST:

   ```php
   POST /rest/V1/order//invoice
   {
     "items": [
       {
         "order_item_id": 2,
         "qty": 1
       }
     ]
   }
   ```

<u>Resultados esperados</u>:

La factura parcial se crea para un pedido realizado con el **Pago a cuenta** método de pago, según lo esperado.

<u>Resultados reales</u>:

La API de REST devuelve el siguiente error:

```php
{"message":"Invoice Document Validation Error(s):\nAn invoice for partial quantities cannot be issued for this order. To continue, change the specified quantity to the full quantity."}
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos, según el producto de Adobe Commerce:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en la herramienta QPT, consulte la [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
