---
title: "MDVA-39163: Métodos de envío no disponibles para los usuarios recién registrados con productos de la sesión de invitado"
description: El parche MDVA-39163 soluciona el problema de que los métodos de envío no están disponibles cuando se registra un nuevo usuario y los productos del carro de compras proceden de la sesión de invitado. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9. El ID del parche es MDVA-39163. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: f8661a4e-5832-41bb-be3d-4ea6c863fdb9
feature: CMS, Marketing Tools, Orders, Products, Shipping/Delivery
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# MDVA-39163: métodos de envío no disponibles para los usuarios recién registrados con productos de la sesión de invitado

El parche MDVA-39163 soluciona el problema de que los métodos de envío no están disponibles cuando se registra un nuevo usuario y los productos del carro de compras proceden de la sesión de invitado. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9. El ID del parche es MDVA-39163. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los métodos de envío no están disponibles cuando se registra el nuevo usuario y los productos del carro de compras proceden de la sesión de invitado.

<u>Pasos a seguir</u>:

1. Vaya a **Administración** > **Tiendas** > **Configuración** > **Ventas** > **Métodos de envío**. Habilita solo el método de envío de **tarifa fija** y deshabilita todo lo demás.
1. En el método de envío **Tarifa fija**, selecciona la opción de país **Específico** disponible en la opción **Enviar a países aplicables** y selecciona un país de la lista (por ejemplo, Estados Unidos).
1. Vaya a **Administración** > **Tiendas** > **Configuración** > **Cliente** > **Configuración del cliente** y establezca **Requerir confirmación por correo electrónico** en _Sí_.
1. Cree una nueva plantilla de correo electrónico en **Admin** > **Marketing** > **Plantillas de correo electrónico**, cargue la plantilla `Footer (magento/luma)` y reemplace el contenido de la plantilla por un bloque de CMS.

   ```CMS
   {{block class="Magento\Cms\Block\Block" block_id="footer_links_block"}}
   ```

1. Vaya a **Administración** > **Contenido** > **Diseño** > **Configuración** y seleccione el tema relacionado con su sitio web de front-end. Establezca la &quot;Plantilla de pie de página&quot; en la nueva plantilla de correo electrónico creada.
1. Vaya al front-end y añada un producto al carro de compras.
1. Cree un cliente; recibirá un correo electrónico para confirmar la dirección de correo electrónico. Haga clic en el vínculo de verificación. Se iniciará sesión en el sitio web.
1. Vaya a **Mi cuenta** y agregue una dirección. Establezca la dirección del país de envío en el país de envío establecido anteriormente en la configuración de administración.
1. Vaya a Pago y envío.

<u>Resultados esperados</u>:

El método de envío está disponible, ya que el cliente tiene una dirección compatible con el país de envío.

<u>Resultados reales</u>:

El método de envío no está disponible.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/usage) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en nuestra documentación para desarrolladores.
