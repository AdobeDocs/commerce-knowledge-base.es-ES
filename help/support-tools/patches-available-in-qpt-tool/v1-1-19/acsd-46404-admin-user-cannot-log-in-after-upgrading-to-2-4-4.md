---
title: "ACSD-46404: el usuario administrador no puede iniciar sesión después de actualizar a 2.4.4"
description: El parche ACSD-46404 resuelve el problema en el que un usuario administrador no puede iniciar sesión después de actualizar a 2.4.4. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.19. El ID del parche es ACSD-46404. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.5.
exl-id: 0aebc879-1128-4be2-a6a8-90d5812c7602
feature: Admin Workspace
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# ACSD-46404: el usuario administrador no puede iniciar sesión después de actualizar a 2.4.4

El parche ACSD-46404 resuelve el problema en el que un usuario administrador no puede iniciar sesión después de actualizar a 2.4.4. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.19 está instalado. El ID del parche es ACSD-46404. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.4-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario administrador no puede iniciar sesión después de actualizar a 2.4.4.

<u>Pasos a seguir</u>:

1. Inicie sesión en el panel de administración
1. Vaya a Tienda > **Configuración** > **Configuración** > **Avanzadas** > **Sistema** > **Seguridad**.
1. Establezca el Tamaño máximo de sesión en el Admin en **0** y guárdelo.

<u>Resultados esperados</u>:

El usuario administrador puede iniciar sesión correctamente.

<u>Resultados reales</u>:

El usuario administrador cerrará la sesión y no podrá iniciarla.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
