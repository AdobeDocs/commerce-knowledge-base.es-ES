---
title: "MDVA-42326: Los clientes obtienen un error al cerrar la compra después del tiempo de espera de sesión"
description: El parche MDVA-42326 resuelve el problema en el que los clientes obtienen un error al realizar la compra después del tiempo de espera de sesión, incluso si el carro de compras persistente está habilitado. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8. El ID del parche es MDVA-42326. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: bc9b71de-510d-4c4e-8b0d-9abf9a3e447f
feature: Checkout, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-42326: Los clientes obtienen un error al cerrar la compra después del tiempo de espera de sesión

El parche MDVA-42326 resuelve el problema en el que los clientes obtienen un error al realizar la compra después del tiempo de espera de sesión, incluso si el carro de compras persistente está habilitado. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8. El ID del parche es MDVA-42326. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los clientes reciben un error en el cierre de compra después del tiempo de espera de sesión, incluso si el carro de compras persistente está habilitado.

<u>Requisitos previos</u>:

1. Vaya a **Configuración** > **General** > **Web** > **Configuración de cookies predeterminada** > **Duración de la cookie** y establézcala en **120**.
1. Vaya a **Configuración** > **Clientes** > **Configuración del cliente** > **Opciones de clientes en línea** y establezca ambos valores en **2**.
1. Vaya a **Configuración** > **Clientes** > **Carro de compras persistente** y establézcalo en **Habilitar**.
1. Vaya a **Configuración** > **Ventas** > **Métodos de pago** y desactive todos los métodos de pago excepto **Cheque/Giro postal** (debe habilitarse).

<u>Pasos a seguir</u>:

1. Inicie sesión como cliente y añada algunos productos al carro de compras.
1. Compruebe el carro de compras.
1. Espere dos minutos (configurado como condición previa); la sesión debe agotarse.
1. Haga clic en **Ir a cierre de compra** y no actualice la página.
1. Compra como invitado, rellena la dirección de envío y elige una forma de envío.
1. Haga clic en **Siguiente**.
1. En la página **Revisar y pagar**, haz clic en **Realizar pedido**. Dado que solo se permite un método de pago, el cliente debe poder realizar el pedido sin seleccionar el método de pago.

<u>Resultados esperados</u>:

El cliente debe poder realizar el pedido.

<u>Resultados reales</u>:

El cliente recibe el siguiente error: *Error de validación de dirección: el correo electrónico tiene un formato incorrecto*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/usage) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en nuestra documentación para desarrolladores.
