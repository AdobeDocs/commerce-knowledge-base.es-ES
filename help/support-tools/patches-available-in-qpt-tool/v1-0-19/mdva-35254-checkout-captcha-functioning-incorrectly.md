---
title: "MDVA-35254: El CIERRE DE COMPRA DE CAPTCHA funciona incorrectamente"
description: El parche MDVA-35254 corrige el problema con los campos CAPTCHA, que no se muestran tras un número incorrecto de intentos de pago de terceros. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. El ID del parche es MDVA-35254. Tenga en cuenta que el problema se corrigió en la versión 2.4.3 de Adobe Commerce.
exl-id: 226c672b-3740-4a87-9ea1-66892acb9fe2
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-35254: Cierre de compra de CAPTCHA que funciona incorrectamente

El parche MDVA-35254 corrige el problema con los campos CAPTCHA, que no se muestran tras un número incorrecto de intentos de pago de terceros. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 está instalado. El ID del parche es MDVA-35254. Tenga en cuenta que el problema se corrigió en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en la infraestructura en la nube 2.4.1

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.1-2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir</u>:

Configurar CAPTCHA:

1. Instale y configure un proveedor de pagos de terceros (Ejemplo: Braintree).
1. Ir a **Tienda > Configuración > Cliente > Configuración del cliente > CAPTCHA > Forms**.
1. Seleccionar **Cierre de compra/Colocación de pedido**.
1. Guarde el **Número de intentos incorrectos de inicio de sesión** como valor predeterminado (predeterminado = *3*).
1. Inicie sesión como cliente.
1. Añada cualquier producto al carro de compras.
1. Vaya a la sección de pago en el cierre de compra.
1. Seleccionar **Tarjeta de crédito** método de pago (ejemplo: Braintree).
1. Realiza tres intentos de pago fallidos.

<u>Resultados esperados</u>:

El campo CAPTCHA se muestra cuando se alcanza el número de intentos fallidos.

<u>Resultados reales</u>:

El campo CAPTCHA nunca se muestra, solo el mensaje de error: *Proporcione el código CAPTCHA e inténtelo de nuevo.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
