---
title: "Parche MDVA-33704: no se muestra la captación en tienda"
description: El parche MDVA-33704 soluciona el problema de que los productos con opción de recogida en tienda no se muestren como método de envío.
exl-id: 2c5c7627-5d2e-44d2-9579-314dbd31ee8b
feature: Shipping/Delivery
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Parche MDVA-33704: no se muestra la captación en tienda

El parche MDVA-33704 soluciona el problema de que los productos con opción de recogida en tienda no se muestren como método de envío.

Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. El ID del parche es MDVA-33704. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:** Adobe Commerce en la infraestructura en la nube 2.4.0-p1

**Compatible con versiones de Adobe Commerce:** Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.4.0-2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Requisito previo</u>:<br>

**Seleccionar en tienda** habilitado

<u>Pasos a seguir</u>:

1. Añadir un producto al carro de compras.
1. Vaya a Cierre de compra.
1. Agrega la información de envío y elige cualquier método de envío que no sea la recogida en la tienda.
1. Seleccione **Continuar con el pago**, pero luego no continuar con la página de pago.
1. En su lugar, vuelva a la sección **Contacto y envío**.
1. Seleccionar **recogida**.
1. Seleccione **Tienda** y **Haga clic para pagar**.
1. Tenga en cuenta que la dirección de envío se introduce automáticamente como dirección de facturación.
1. Actualice la página web.

<u>Resultados esperados</u>:

La opción de recogida en tienda se mostrará como un método de envío, según lo esperado.

<u>Resultados reales</u>:

La opción de recogida en tienda no se mostrará como método de envío.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en la herramienta QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
