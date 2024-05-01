---
title: "ACSD-50345: problemas de reCAPTCHA durante el cierre de compra"
description: Aplique el parche ACSD-50345 para corregir el problema de Adobe Commerce en el que las validaciones reCAPTCHA v2 y v3 fallan al realizar pedidos y durante el cierre de compra.
exl-id: ac8c8130-0e4d-4610-9a55-afa779cce7a0
feature: Checkout, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-50345: problemas de reCAPTCHA durante el cierre de compra

El parche ACSD-50345 corrige el problema en el que las validaciones de reCAPTCHA v2 y v3 fallan al realizar pedidos y durante el cierre de compra. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.31 está instalado. El ID del parche es ACSD-50345. Tenga en cuenta que el problema se solucionó parcialmente en Adobe Commerce 2.4.6 y se ha programado que se corrija completamente en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.5-p2

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

**#1 de caso**

Google reCAPTCHA v2 no se vuelve a cargar después de enviar un pago fallido.

<u>Pasos a seguir</u>

1. Configurar **[!UICONTROL Google reCAPTCHA v2]** (*No soy un robot*).
1. Habilite la **[!UICONTROL reCAPTCHA]** para pago y envío.
1. Intente realizar un pedido sin hacer clic en **[!UICONTROL reCAPTCHA]**.
1. Una vez que el usuario recibe el mensaje de error del reCAPTCHA que falta (*Error de validación de reCAPTCHA, vuelva a intentarlo*), haga clic en **[!UICONTROL reCAPTCHA]** y luego intente hacer un pedido.

<u>Resultados esperados</u>

El pedido no se realizará con un reCAPTCHA incorrecto.

<u>Resultados reales</u>

Se genera un error: *Error de validación de reCAPTCHA, vuelva a intentarlo* y *No existe ese carro con id = 4*

**#2 de caso**

Google reCAPTCHA v3 Invisible no funciona en el cierre de compra y no se puede realizar el pedido. `PlaceOrder` no se activa el evento.

<u>Pasos a seguir</u>

1. Configure las variables **[!UICONTROL reCAPTCHA v3 Invisible]** desde el **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]**.
1. Activar **[!UICONTROL reCAPTCHA v3 Invisible]** para pago y envío/colocación de un pedido en **[!UICONTROL Storefront]** pestaña.
1. Intente realizar un pedido con el [!UICONTROL Check/Money order] forma de pago.

<u>Resultados esperados</u>

El pedido debe realizarse con el **[!UICONTROL reCAPTCHA]** se encendió.

<u>Resultados reales</u>

Después de hacer clic en **[!UICONTROL Place Order]** botón, se desactiva y no ocurre nada más.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
