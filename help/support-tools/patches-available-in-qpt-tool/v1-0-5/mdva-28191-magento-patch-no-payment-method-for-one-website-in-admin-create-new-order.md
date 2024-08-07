---
title: "MDVA-28191: No hay forma de pago para un sitio web en Administración Crear nuevo pedido"
description: El parche MDVA-28191 soluciona el problema de que no se carga un método de pago en Admin **Crear nuevo pedido** para un sitio web, aunque es posible que se muestren métodos de pago para otros sitios web.  Este parche está disponible cuando está instalada la herramienta [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) versión 1.0.5.
exl-id: 42169743-4f09-4f0a-aadd-931cccc9b467
feature: Admin Workspace, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-28191: No hay forma de pago para un sitio web en Administración Crear nuevo pedido

El parche de MDVA-28191 soluciona el problema que consiste en que no se está cargando un método de pago en Admin **Crear nuevo pedido** para un sitio web, aunque es posible que se muestren métodos de pago para otros sitios web.  Esta revisión está disponible cuando está instalada la herramienta [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) versión 1.0.5.

## Productos y versiones afectados

Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.3 a 2.4.1 (incluido 2.3.5-p1).

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al crear un pedido desde el backend, Adobe Commerce crea dos comillas, una está inactiva y la otra activa. Sin embargo, la sesión contiene el ID de cotización inactivo.

<u>Pasos a seguir</u>

1. Vaya a **Panel de administración** > **Ventas** > **Pedidos** y haga clic en el botón **Crear nuevo pedido**.
1. Seleccione el cliente para el que desea crear el pedido.
1. Si la tienda tiene varias vistas, elige la vista de la tienda en la que se realizará el pedido, en la página **Crear nuevo pedido** para el usuario que seleccionaste.
1. Agregue productos de la sección **Actividades del cliente** o del catálogo haciendo clic en **Agregar productos**. Desplácese hacia abajo por la página para completar las secciones siguientes según sea necesario para el pedido:
   * Aplicar códigos de cupones
   * Método de pago
   * Método de envío
   * Comentarios del pedido

<u>Resultado esperado:</u>

Las formas de pago deben cargarse en Admin para todos los sitios web.

<u>Resultado real:</u>

No hay ningún método de pago disponible (ni se muestra el mensaje &quot;*No se requiere información de pago*&quot;) para este sitio web, aunque los métodos de pago pueden mostrarse al probar pedidos para otros sitios web.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
