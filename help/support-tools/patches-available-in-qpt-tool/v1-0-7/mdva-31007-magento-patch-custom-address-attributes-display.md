---
title: "MDVA-31007: se muestran los atributos de dirección personalizados"
description: El parche MDVA-31007 soluciona el problema de que los atributos de dirección personalizados no se muestran correctamente en la página de detalles del pedido en el área Mi cuenta y en el backend (en la ubicación **Ventas &gt; Pedidos**). Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.
exl-id: 43c82b66-395f-4e33-8312-9a1994862f5f
feature: Attributes, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# MDVA-31007: visualización de atributos de dirección personalizados

El parche de MDVA-31007 soluciona el problema de que los atributos de dirección personalizados no se muestran correctamente en la página de detalles del pedido en el área Mi cuenta y en el backend (en la ubicación **Ventas > Pedidos**). Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce en infraestructura en la nube 2.4.0

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir</u>:

1. Inicie sesión en el servidor de administración.
1. Vaya a **Tiendas** > **Atributos** > **Direcciones de clientes**.
1. Cree dos atributos:

   * Establecer tipo de entrada: *Lista desplegable*.
   * Establecer tipo de entrada: *Texto*.

1. Vaya a **Tiendas** > **Configuraciones** > **Cliente** > **Configuraciones de cliente**.
1. Seleccione *Ámbito* como **Tienda predeterminada** vista.
1. Expanda la sección **Plantilla de dirección**. Actualice *Texto*, *Texto Una Línea* y *HTML* para incluir los dos atributos personalizados anteriores:

   ```php
   {{depend testdropdown}}Dropdown: {{var testdropdown}}{{/depend}}    {{depend testtext}}Text: {{var testtext}}{{/depend}}
   ```

1. Abra Storefront.
1. Crear e iniciar sesión con un usuario.
1. Vaya a **Mi cuenta** > **Libreta de direcciones** y agregue una nueva dirección (rellene los dos atributos personalizados).
1. Añada un producto al carro de compras y realice un pedido.
1. En la página de pedidos realizados correctamente, haga clic en el vínculo **Número de pedido**.
1. En la página de detalles del pedido, observe la sección **Información del pedido**.
1. Vaya a **Servidor** > **Ventas** > **Pedidos**, haga clic en el pedido anterior y observe la sección **Información de dirección**.

<u>Resultados esperados</u>:

Tanto en el front-end como en el back-end, la dirección de facturación y envío se muestra según lo esperado.

<u>Resultados reales</u>:

Tanto en el front-end como en el back-end, la dirección de facturación no se muestra correctamente. Falta la opción seleccionada del atributo desplegable y el valor del atributo de entrada contiene el código de atributo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
