---
title: "MDVA-37364: El atributo de cliente personalizado del tipo de fecha rompe la interfaz de usuario de la cuadrícula"
description: El parche MDVA-37364 resuelve el problema en el que el atributo de cliente personalizado de tipo de fecha rompe la interfaz de usuario de la cuadrícula del cliente. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. El ID del parche es MDVA-37364. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.4 de Adobe Commerce.
exl-id: d25baabf-45eb-403c-9f88-9c2448cc7b49
feature: Attributes, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MDVA-37364: atributo de cliente personalizado de tipo de fecha rompe la IU de la cuadrícula

El parche MDVA-37364 resuelve el problema en el que el atributo de cliente personalizado de tipo de fecha rompe la interfaz de usuario de la cuadrícula del cliente. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. El ID del parche es MDVA-37364. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.4 de Adobe Commerce.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0-2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El atributo de cliente personalizado del tipo de fecha rompe la interfaz de usuario de cuadrícula del cliente.

<u>Pasos a seguir</u>:

1. Cree un atributo personalizado con tipo de fecha:
   * Vaya a **Tiendas** > **Atributos** > **Agregar atributo**.
   * Establezca el Tipo de entrada en Fecha.
   * Establezca las Opciones de Agregar a columna en Sí.
   * Guarde el atributo.
1. Vaya a **Administración** > **Clientes** > **Todos los clientes**.
   * Agregue el atributo personalizado recién agregado a la cuadrícula desde la opción Columnas.
1. Cree/edite un cliente y establezca el valor del campo de atributo de fecha personalizado creado.
1. Guarde, reindexe y borre la caché.
1. Vaya a **Clientes** > **Todos los clientes**.
   * Marque la cuadrícula de cliente.

<u>Resultados esperados</u>:

La cuadrícula de cliente de administración muestra todos los datos, incluido el nuevo atributo personalizado de fecha, sin interrumpir la interfaz de usuario de la cuadrícula de cliente.

<u>Resultados reales</u>:

La IU de la cuadrícula del cliente de administración está dañada.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos en función del tipo de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/usage) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
