---
title: "MDVA-41236: No se pueden crear nuevas actualizaciones programadas o editar las existentes para el producto"
description: El parche de MDVA-41236 soluciona el problema en el que los usuarios no pueden crear actualizaciones programadas nuevas o editar las existentes para el producto si se ha eliminado anteriormente la "Fecha de finalización". Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5. El ID del parche es MDVA-41236. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: 00d6c0af-f248-49f6-aaa2-3ae3c0294832
feature: Products, Staging
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# MDVA-41236: No se pueden crear nuevas actualizaciones programadas o editar las existentes para el producto

El parche de MDVA-41236 soluciona el problema en el que los usuarios no pueden crear actualizaciones programadas nuevas o editar las existentes para el producto si se ha eliminado anteriormente la &quot;Fecha de finalización&quot;. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5. El ID del parche es MDVA-41236. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios no pueden crear nuevas programaciones o editar las existentes para productos si la &quot;Fecha de finalización&quot; se ha eliminado anteriormente.

<u>Pasos a seguir</u>:

1. Cree un producto con el estado establecido en *deshabilitar*.
1. Añada una actualización programada para habilitar este producto.
   * Añadir fechas de inicio y finalización futuras.
1. Edite la actualización programada eliminando **End Date**.
1. Vuelva a editar la programación e intente agregar una **Fecha de finalización**. Se producirá un error.
1. Actualice la página y vuelva a **Editar actualización programada**.
1. Haga clic en **Eliminar de la actualización** > **Eliminar la actualización**.
1. Ahora no debería ver la actualización programada en la parte superior de la página de edición del producto.
1. Intente crear una nueva actualización programada que se superponga a la duración anterior.

<u>Resultados esperados</u>:

* No hay ningún error en el paso 4. El administrador puede actualizar la actualización programada sin ningún error, ya que la programación aún no está activa.
* El usuario administrador puede eliminar la actualización anterior y crear una nueva.

<u>Resultados reales</u>:

Los usuarios reciben el siguiente mensaje de error:

*error: ya existe una actualización futura en este intervalo de tiempo. Establezca un intervalo diferente e inténtelo de nuevo.*


## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/usage) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
