---
title: "MDVA-43091: No se puede solicitar el producto empaquetado al administrador"
description: El parche MDVA-43091 resuelve el problema en el que los usuarios no pueden solicitar el producto empaquetado al administrador de Commerce. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10. El ID del parche es MDVA-43091. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: 77dff356-4f75-4b06-b62b-5379a4eec273
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# MDVA-43091: No se puede solicitar el producto empaquetado al administrador

El parche MDVA-43091 resuelve el problema en el que los usuarios no pueden solicitar el producto empaquetado al administrador de Commerce. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10. El ID del parche es MDVA-43091. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al intentar solicitar el producto agrupado al administrador, se produce el siguiente error: *No puede utilizar la cantidad decimal para este producto.*

<u>Pasos a seguir</u>:

1. Instale un Adobe Commerce limpio.
1. Cree dos productos simples.
1. Cree un producto agrupado con dos opciones.
1. Cree una cuenta de cliente en el front-end.
1. Vaya a **Administración** > **Ventas** > **Pedidos** > **Crear nuevo pedido**.
   * Seleccione la cuenta de cliente creada justo ahora.
   * Intente agregar el producto agrupado al carro de compras.

<u>Resultados esperados</u>:

El usuario administrador puede añadir el producto con una cantidad al carro de compras.

<u>Resultados reales</u>:

El usuario administrador recibe el siguiente error: *No se puede usar la cantidad decimal para este producto.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/usage) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en nuestra documentación para desarrolladores.
