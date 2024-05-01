---
title: "Parche de MDVA-34192: no se pueden modificar las fechas de los clientes en un formato determinado"
description: El parche MDVA-34192 corrige el problema en el que es imposible modificar/especificar la fecha de nacimiento del cliente con el formato dd/mm/aaaa. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.
exl-id: 8aa36970-b2bf-43f8-ba8f-bfc144f8d4ab
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# Parche de MDVA-34192: no se pueden modificar las fechas de los clientes en un formato determinado

El parche MDVA-34192 corrige el problema en el que es imposible modificar/especificar la fecha de nacimiento del cliente con el formato dd/mm/aaaa. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 está instalado. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:** Adobe Commerce en infraestructura en la nube 2.3.5-p1

**Compatible con las versiones de Adobe Commerce:** 2.3.4-2.3.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El parche soluciona varios problemas. A continuación se muestran la descripción y los pasos a seguir para reproducir uno de ellos.

El filtro de cuadrícula de producto no funciona correctamente cuando filtramos con un atributo de fecha personalizado y la configuración regional del usuario administrador es en\_GB.

<u>Pasos a seguir:</u>:

1. Crear un usuario administrador cuyo **Configuración regional de interfaz** se establece en *Inglés (Reino Unido)*.
1. Cree un atributo de fecha con la configuración siguiente:
   * **Tipo de entrada de catálogo del propietario de la tienda**: *Fecha*
   * **Uso en opciones de filtro**: *Sí*
   * **Agregar a opciones de columna**: *Sí*
1. Asigne el atributo a un conjunto de atributos.
1. Vaya a la página de edición del producto, seleccione una fecha para el nuevo atributo con el selector de fechas y guarde.
1. Intente filtrar la cuadrícula de producto con el nuevo atributo de fecha.

<u>Resultado esperado:</u>:

El filtro de producto funciona correctamente para un atributo de fecha personalizado cuando la configuración regional del usuario administrador es en\_GB.

<u>Resultado real:</u>:

El filtro de producto no funciona correctamente para un atributo de fecha personalizado cuando la configuración regional del usuario administrador es en\_GB.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos, según el producto de Adobe Commerce:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en la herramienta QPT, consulte la [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
