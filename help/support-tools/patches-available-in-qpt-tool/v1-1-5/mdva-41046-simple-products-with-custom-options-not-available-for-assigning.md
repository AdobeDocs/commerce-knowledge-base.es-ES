---
title: "MDVA-41046: No se pueden asignar productos simples con opciones personalizadas"
description: El parche MDVA-41046 resuelve el problema en el que los productos simples con opciones personalizadas no están disponibles para asignarlos a productos configurables o agrupados. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5. El ID del parche es MDVA-41046. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: 01229a69-c72a-4189-9be5-1761073b74ee
feature: Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-41046: No se pueden asignar productos simples con opciones personalizadas

El parche MDVA-41046 resuelve el problema en el que los productos simples con opciones personalizadas no están disponibles para asignarlos a productos configurables o agrupados. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5. El ID del parche es MDVA-41046. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los productos simples con opciones personalizadas no están disponibles para asignarlos a productos configurables o agrupados.

<u>Pasos a seguir</u>:

1. Cree un producto simple con opciones personalizables y establezca un valor para el atributo configurable.
   * Use *Color* como atributo configurable y seleccione *Amarillo* como valor de color.
1. Guarde el producto simple.
1. Ahora vaya a la página Crear producto configurable.
1. Pase por el asistente &quot;Crear configuración&quot; y asegúrese de seleccionar *Amarillo* como color de atributo.
1. Sin guardar el producto configurable, seleccione la opción &quot;Elegir producto diferente&quot; en la lista desplegable Seleccionar.
1. Se abrirá una cuadrícula de producto filtrada por el atributo de color amarillo. Ahora seleccione el producto simple que se creó anteriormente con opciones personalizables.
1. Guarde el producto configurable.

<u>Resultados esperados</u>:

El producto simple con opciones personalizadas está disponible para asignar (visible en la cuadrícula) en el paso 6.

<u>Resultados reales</u>:

La sección de configuración está vacía.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
