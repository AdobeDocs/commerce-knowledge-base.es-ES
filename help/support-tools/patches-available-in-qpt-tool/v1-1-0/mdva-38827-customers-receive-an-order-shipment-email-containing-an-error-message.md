---
title: "MDVA-38827: Los clientes reciben un error de envío de pedidos por correo electrónico"
description: '"El parche de MDVA-38827 soluciona el problema en el que los clientes reciben un correo electrónico de envío de pedidos que contiene el siguiente mensaje de error: *Lo sentimos, se ha producido un error al generar este contenido*. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.0. El ID del parche es MDVA-38827. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4".'
exl-id: f2e5aeab-7d46-46be-9631-c3a863d9bf52
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-38827: Los clientes reciben un error de envío de pedidos por correo electrónico

El parche MDVA-38827 corrige el problema en el que los clientes reciben un correo electrónico de envío de pedidos que contiene el siguiente mensaje de error: *Se ha producido un error al generar este contenido*. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.0 está instalado. El ID del parche es MDVA-38827. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.4.2-p1

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando se selecciona la opción Notificar a los clientes por correo electrónico para el envío, los clientes reciben un correo electrónico con el siguiente mensaje de error: *Se ha producido un error al generar este contenido*.

<u>Pasos a seguir</u>:

1. Ir a **Marketing** > **Comunicaciones** > **Plantillas de correo electrónico** y seleccione **Añadir nueva plantilla**.
   * Seleccionar **Ventas del Magento** > **Nuevo envío**.
   * Haga clic en **Cargar plantilla**.
   * Añada un nombre de plantilla (por ejemplo, Plantilla de envíos principal) y haga clic en **Guardar**.
1. Ir a **Almacenar** > Configuración > **Configuración** > **Ventas** > **Correo electrónico de ventas**:
   * Activar **Comentarios del envío**.
   * Seleccionar **Plantilla de envíos principal** (consulte la parte &quot;Añadir un nombre de plantilla&quot; del paso 1) en Plantilla de correo electrónico de comentario de envío y Plantilla de correo electrónico de comentario de envío para invitado.
1. Haga un pedido. Vaya al panel Administración > **Ventas** > **Pedido**, haga clic en **Ver** y, a continuación, envíe el pedido.
1. El estado del pedido cambiará de Pendiente a Procesamiento.
1. Clic **Envíos** en el menú de la barra lateral izquierda y haga clic en **Ver** para ver el pedido.
1. Agregar un comentario en **Texto del comentario** abajo **Historial de envíos** y marque la casilla **Notificar al cliente por correo electrónico**.
1. Clic **Enviar comentario**.

<u>Resultados esperados</u>:

Se genera un correo electrónico de ventas con comentarios sobre el envío.

<u>Resultados reales</u>:

Se recibe el siguiente mensaje de error en el correo electrónico: *Lo sentimos, se ha producido un error al generar este contenido.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
