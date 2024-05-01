---
title: "MDVA-39163: Métodos de envío no disponibles para los usuarios recién registrados con productos de la sesión de invitado"
description: El parche MDVA-39163 soluciona el problema de que los métodos de envío no están disponibles cuando se registra un nuevo usuario y los productos del carro de compras proceden de la sesión de invitado. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9. El ID del parche es MDVA-39163. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: f8661a4e-5832-41bb-be3d-4ea6c863fdb9
feature: CMS, Marketing Tools, Orders, Products, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# MDVA-39163: métodos de envío no disponibles para los usuarios recién registrados con productos de la sesión de invitado

El parche MDVA-39163 soluciona el problema de que los métodos de envío no están disponibles cuando se registra un nuevo usuario y los productos del carro de compras proceden de la sesión de invitado. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 está instalado. El ID del parche es MDVA-39163. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los métodos de envío no están disponibles cuando se registra el nuevo usuario y los productos del carro de compras proceden de la sesión de invitado.

<u>Pasos a seguir</u>:

1. Ir a **Administrador** > **Tiendas** > **Configuración** > **Ventas** > **Métodos de envío**. Habilite solo el **Tarifa plana** método de envío y deshabilitar todo lo demás.
1. En el **Tarifa plana** método de envío, seleccione **Específico** opción de país disponible en la **Enviar a los países aplicables** y seleccione un país de la lista (por ejemplo, Estados Unidos).
1. Ir a **Administrador** > **Tiendas** > **Configuración** > **Cliente** > **Configuración del cliente** y establecer **Requerir confirmación de correo electrónico** hasta _Sí_.
1. Creación de una nueva plantilla de correo electrónico en **Administrador** > **Marketing** > **Plantillas de correo electrónico** y cargar `Footer (magento/luma)` y reemplace el contenido de la plantilla con un bloque CMS.

   ```CMS
   {{block class="Magento\Cms\Block\Block" block_id="footer_links_block"}}
   ```

1. Ir a **Administrador** > **Contenido** > **Diseño** > **Configuración** y seleccione el tema relacionado con el sitio web de front-end. Establezca la &quot;Plantilla de pie de página&quot; en la nueva plantilla de correo electrónico creada.
1. Vaya al front-end y añada un producto al carro de compras.
1. Cree un cliente; recibirá un correo electrónico para confirmar la dirección de correo electrónico. Haga clic en el vínculo de verificación. Se iniciará sesión en el sitio web.
1. Ir a **Mi cuenta** y añada una dirección. Establezca la dirección del país de envío en el país de envío establecido anteriormente en la configuración de administración.
1. Vaya a Pago y envío.

<u>Resultados esperados</u>:

El método de envío está disponible, ya que el cliente tiene una dirección compatible con el país de envío.

<u>Resultados reales</u>:

El método de envío no está disponible.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
