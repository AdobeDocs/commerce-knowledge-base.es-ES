---
title: "ACSD-54264: Error cuando el cliente intenta cerrar la compra con un presupuesto negociable"
description: 'Aplique el parche ACSD-54264 para corregir el problema de Adobe Commerce donde aparece un mensaje de error "No puede actualizar el atributo solicitado. ID de fila: "store_id" aparece cuando un cliente intenta realizar una compra con una oferta negociable de otra vista de tienda.'
feature: B2B, Checkout
role: Admin, Developer
exl-id: de8f451e-3b0a-4721-9ff4-18553477db1d
source-git-commit: 2e344b1ca4bc075bdbc9074bb431a398f0871698
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-54264: Aparece un error cuando el cliente intenta pagar con un presupuesto negociable

El parche ACSD-54264 corrige el problema donde un mensaje de error *No se puede actualizar el atributo solicitado. Id. de fila: store_id* aparece cuando un cliente intenta realizar la retirada con una oferta negociable de otra vista de tienda. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42. El ID del parche es ACSD-54264. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Mensaje de error *No se puede actualizar el atributo solicitado. Id. de fila: store_id* aparece cuando un cliente intenta realizar la retirada con una oferta negociable de otra vista de tienda.

<u>Requisitos previos</u>:

Los módulos B2B de Adobe Commerce están instalados y habilitados.

<u>Pasos a seguir</u>:

1. Cree una vista de tienda adicional para el sitio web predeterminado.
1. Habilite *[!UICONTROL B2B Quote]* en la configuración.
1. Inicie sesión como cliente de la empresa en una de las vistas de la tienda.
1. Agregar un producto a *[!UICONTROL Shopping Cart]*.
1. Envíe el presupuesto para su revisión.
1. Como usuario administrador, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** y envíe el presupuesto aprobado.
1. Como cliente de la compañía, cambie la vista de la tienda a otra vista de la tienda.
1. Trate de verificar.

<u>Resultados esperados</u>:

El cliente realiza un pedido con esta oferta.

<u>Resultados reales</u>:

* El error se produce al guardar la información de envío:

  `You cannot update the request attribute. Row ID: store_id =#`

* Se registra el siguiente error:

  `report.CRITICAL: Magento\Framework\Exception\InputException: You cannot update the requested attribute. Row ID: store_id = 2. in /app/code/Magento/NegotiableQuote/Plugin/Quote/Model/QuoteUpdateValidator.php:100`

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
