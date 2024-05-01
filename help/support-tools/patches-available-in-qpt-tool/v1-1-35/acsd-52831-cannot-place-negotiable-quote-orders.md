---
title: 'ACSD-52831: No se pueden realizar pedidos de presupuesto negociables cuando [!DNL Google reCAPTCHA v3 Invisible] enabled'
description: Aplique el parche ACSD-52831 para solucionar el problema de Adobe Commerce en el que no puede realizar pedidos de presupuesto negociables cuando [!DNL Google reCAPTCHA v3 Invisible] está activada.
feature: Quotes, B2B, Checkout
role: Admin
exl-id: 80cf5592-0784-4b37-8373-abec0847a9f0
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-52831: No se pueden realizar pedidos de presupuesto negociables cuando [!DNL Google reCAPTCHA v3 Invisible] activado

El parche ACSD-52831 corrige el problema en el que no puede realizar pedidos de presupuesto negociables cuando [!DNL Google reCAPTCHA v3 Invisible] está activada. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.35 está instalado. El ID del parche es ACSD-52831. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

No se pueden realizar pedidos de presupuesto negociables cuando [!DNL Google reCAPTCHA v3 Invisible] está activada.

<u>Pasos a seguir</u>:

1. Habilite la función de presupuesto B2B.
1. Activar [!DNL Google reCAPTCHA v3 Invisible] en la tienda para habilitar el cierre de compra/realización de pedidos.
1. Levante una cotización y proceda al cierre de compra con esa cotización.
1. No podrá realizar un pedido debido al error de CAPTCHA.

<u>Resultados esperados</u>:

La oferta continúa con el cierre de compra.

<u>Resultados reales</u>:

Se obtiene el error *Error de validación de reCAPTCHA, vuelva a intentarlo*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
