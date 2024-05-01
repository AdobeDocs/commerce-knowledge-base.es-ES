---
title: "MDVA-41136: La fecha de caducidad de mage-cache-sessid no se amplía"
description: El parche MDVA-41136 resuelve el problema de que la fecha de caducidad de la cookie "mage-cache-sessid" no se amplía, lo que da como resultado la limpieza de datos del cliente. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. El ID del parche es MDVA-41136. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: 7673d084-1ed2-4f1d-8525-e665b971baf2
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# MDVA-41136: La fecha de caducidad de mage-cache-sessid no se amplía

El parche MDVA-41136 resuelve el problema en el que la fecha de caducidad del `mage-cache-sessid` no se amplía la cookie, lo que provoca la limpieza de datos del cliente. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 está instalado. El ID del parche es MDVA-41136. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La fecha de caducidad del `mage-cache-sessid` no se amplía, lo que provoca la limpieza de datos del cliente.

<u>Pasos a seguir</u>:

1. En Commerce Admin, vaya a **Tiendas** > **Configuración** > **Web** > **Configuración de cookie predeterminada** > y establecer **Duración de cookie** a 60.
1. Inicie sesión como cliente en la tienda.
1. Ir a **Mi cuenta**.
1. Vuelva a cargar la página después de 30 segundos.

<u>Resultados esperados</u>:

Se muestra el nombre del cliente en el encabezado.

<u>Resultados reales</u>:

Falta el nombre del cliente en el encabezado y la variable *Mensaje de bienvenida predeterminado.* se muestra el mensaje.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
