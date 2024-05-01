---
title: "MDVA-34474: La actualización de la lista de solicitudes de API genera un error"
description: El parche MDVA-34474 corrige el problema en el que, al añadir un producto a la lista de solicitudes mediante API, se produce un error. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. El ID del parche es MDVA-34474. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.
exl-id: dc39c4f7-417c-45ea-914c-32f7305527da
feature: REST, B2B
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# MDVA-34474: La actualización de la lista de solicitudes de API genera un error

El parche MDVA-34474 corrige el problema en el que, al añadir un producto a la lista de solicitudes mediante API, se produce un error. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 está instalado. El ID del parche es MDVA-34474. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.4.0

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.0 - 2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Si se añade un producto a la lista de solicitudes mediante API, se produce un error.

<u>Pasos a seguir</u>:

1. Activar lista de solicitudes en Administración (**Tiendas** > **Configuración** > **General** > **Funciones B2B** > **Activar lista de solicitudes** = *Sí*).
1. Crear un cliente.
1. Crear una nueva lista de solicitudes para esta llamada de envío de cliente ```json    POST rest/all/V1/requisition_lists``` con la carga útil json adjunta.

<u>Resultados esperados</u>:

No hay error y se crea la lista.

<u>Resultados reales</u>:

Error 400.

```json
{"message":"Could not save Requisition List"}
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
