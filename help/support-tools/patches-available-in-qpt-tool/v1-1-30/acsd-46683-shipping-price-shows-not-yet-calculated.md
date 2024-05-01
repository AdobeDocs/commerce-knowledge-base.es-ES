---
title: "ACSD-46683: El precio de envío se muestra *Aún no se ha calculado*"
description: Aplique el parche ACSD-46683 para solucionar el problema de Adobe Commerce donde el precio de envío indica *Aún no se ha calculado*.
exl-id: 77986612-87b7-4f50-afaf-1cfe9a4feb6f
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-46683: se muestra el precio de envío *Aún no se ha calculado*

El parche ACSD-46683 soluciona el problema en el que se muestra el precio de envío *Aún no se ha calculado*. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 está instalado. El ID del parche es ACSD-46683. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El precio de envío indica *Aún no se ha calculado*.

<u>Requisitos previos</u>:

Los módulos de Adobe Commerce Inventory management (MSI) están instalados.

<u>Pasos a seguir</u>:

1. Cree un producto simple y establezca su precio en *34 $*.
1. Configure el método de envío gratuito.
1. Configure al menos un método de envío más.
1. Ir a **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]** y cree una regla nueva:
   * Nombre = *75 más*
   * Cupón = Ninguno
   * Prioridad = 1
   * Condiciones: El subtotal es igual o mayor que *75 $*
   * Acciones:
      * Aplicar al importe de envío = Sí
      * Descartar reglas subsiguientes = No
      * Envío gratuito = para envíos con artículos coincidentes
1. Crear otra regla de precios de carro de compras:
   * Nombre = *35desactivado*
   * Prioridad = 0
   * Coupon = Specific Coupon
   * Código de cupón = 35off
   * Acciones:
      * Aplicar = Porcentaje de descuento en el precio del producto
      * Importe de descuento = 35
      * Aplicar al importe de envío = No
      * Descartar reglas subsiguientes = Sí
      * Envío gratuito = No
1. Abra la tienda y añada tres productos al carro de compras para que el subtotal supere los 75 $.
1. Continúe con el pago y envío como invitado.
1. En la etapa de envío, seleccione **$0 - envío gratuito** y continúe con la etapa de pago.
1. Compruebe la [!UICONTROL Order Summary] en la etapa de pago. Se ve *[!UICONTROL $0 - Free Shipping - Free]*.
1. Aplicación del código de cupón *35desactivado* Sin embargo, actualizará el subtotal y lo hará en menos de 75 dólares.
1. Marque [!UICONTROL Order Summary] en la etapa de pago.

<u>Resultados esperados</u>:

Se muestra el siguiente mensaje: *El método de envío seleccionado no está disponible. Selecciona otra forma de envío para este pedido.*

<u>Resultados reales</u>:

Se muestra el precio de envío *Aún no se ha calculado*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
