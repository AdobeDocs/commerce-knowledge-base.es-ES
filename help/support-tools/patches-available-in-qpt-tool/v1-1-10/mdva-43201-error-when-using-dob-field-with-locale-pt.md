---
title: "MDVA-43201: Error al utilizar el campo DOB con la configuración regional PT"
description: El parche MDVA-43201 resuelve el problema en el que se produce un error al utilizar el atributo de cliente DOB en el formulario de registro de cliente para la configuración regional en portugués. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10. El ID del parche es MDVA-43201. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: 02979378-adc1-4a1a-93bf-a35ad50e6b80
feature: B2B, Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-43201: Error al utilizar el campo DOB con la configuración regional PT

El parche MDVA-43201 resuelve el problema en el que se produce un error al utilizar el atributo de cliente DOB en el formulario de registro de cliente para la configuración regional en portugués. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10. El ID del parche es MDVA-43201. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando se agrega el atributo de cliente DOB al formulario de registro de cliente para la configuración regional en portugués, el formulario da el error *Argumento 1 pasado a iterator_to_array() debe implementar la interfaz travesable, nulo dado*.

<u>Requisitos previos</u>:

Los módulos B2B están instalados.

<u>Pasos a seguir</u>:

1. Vaya a Administración > **Tiendas** > **Configuración** > **General** > **Opciones de configuración regional**, establezca la configuración regional en **Portugués (Portugal)** y haga clic en **Guardar**.
1. Reindexe y borre la caché.
1. Vaya a **Tiendas** > **Atributo** > **Cliente**.
1. Abra el atributo de cliente DOB y establezca **Mostrar en tienda** en **Sí**.
1. Seleccionar todo del **formulario que se usará en**.
1. Guarde el atributo.
1. Vaya a la página Crear nueva cuenta en el front-end.

<u>Resultados esperados</u>:

El formulario de registro de cliente de la tienda portuguesa no genera ningún error al añadir el atributo DOB.

<u>Resultados reales</u>:

El formulario de registro de cliente de la tienda portuguesa proporciona un error al añadir el atributo DOB.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
