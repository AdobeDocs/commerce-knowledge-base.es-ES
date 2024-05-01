---
title: "MDVA-36464: La configuración de envío de correo electrónico no funciona en el nivel de vista de tienda"
description: El parche de MDVA-36464 soluciona el problema de que la configuración de envío de correo electrónico no funciona en el nivel de vista de tienda. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21. El ID del parche es MDVA-36464. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.
exl-id: cdf7e208-90ee-4711-8407-026da42fe3c8
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-36464: la configuración de envío de correo electrónico no funciona en el nivel de vista de tienda

El parche de MDVA-36464 soluciona el problema de que la configuración de envío de correo electrónico no funciona en el nivel de vista de tienda. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 está instalado. El ID del parche es MDVA-36464. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.4.0-p1

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Requisito previo:</u>

Instale Adobe Commerce limpio.

<u>Pasos a seguir</u>:

1. Crear un sitio web, una tienda y una vista de tienda adicionales (en este ejemplo, el segundo sitio web es *sitio web2*).
1. Deshabilitar **Notificación por correo electrónico** a nivel global en **Almacenar** > **Configuración** > **Avanzadas** > **Sistema** > **Configuración de envío de correo**.
1. Activar **Notificación por correo electrónico** en el *sitio web2* level (**Desactivar comunicaciones por correo electrónico** = *No*).
1. En Administración, cree un nuevo usuario y asígnelo al *sitio web2*.
1. En Administración, en la página de edición del cliente, haga clic en **Restablecer contraseña** para el cliente creado anteriormente en el paso 4.

<u>Resultados esperados</u>:

Tanto la **correo electrónico de bienvenida** y el **restablecer correo electrónico de contraseña** se envían, según lo esperado, porque **Desactivar comunicaciones por correo electrónico** = *No* para el segundo sitio web (ejemplo: *sitio web2*).

<u>Resultados reales</u>:

* El **correo electrónico de bienvenida** después de que no se active la creación del nuevo cliente.
* El **restablecer correo electrónico de contraseña** no se activa.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
