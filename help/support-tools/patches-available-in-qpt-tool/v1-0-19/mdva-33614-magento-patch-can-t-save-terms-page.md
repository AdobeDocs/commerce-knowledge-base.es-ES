---
title: "Parche MDVA-33614: no se puede guardar la página de Términos"
description: "El parche de MDVA-33614 corrige el problema en el que es imposible guardar las ediciones en la página de Términos, ya que Page Builder genera el siguiente error: * Se ha producido un error al iniciar Page Builder. Consulte a su contacto de asistencia técnica*. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. El ID del parche es MDVA-33614. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2."
exl-id: d9b287bb-eab4-4c33-b725-ae0074962447
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# Parche de MDVA-33614: no se puede guardar la página Términos

El parche MDVA-33614 corrige el problema en el que es imposible guardar las ediciones en la página Términos, ya que Page Builder genera el siguiente error: *Se ha producido un error al iniciar Page Builder. Consulte con el contacto de soporte técnico*. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. El ID del parche es MDVA-33614. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:** Adobe Commerce en la infraestructura en la nube 2.4.1

**Compatible con versiones de Adobe Commerce:** Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.4.1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Es imposible guardar las ediciones en la página Términos porque Page Builder genera un error.

<u>Pasos a seguir</u>:

1. En Commerce Admin, vaya a **CONTENIDO** > Elementos > **Páginas**.
1. Seleccione la página Términos.
1. Haga clic en **Editar**.
1. Realice una edición y haga clic en **Guardar**.

<u>Resultado esperado</u>:

La página se guardará sin errores.

<u>Resultado real</u>:

Se muestra el siguiente error: *Se produjo un error al iniciar Page Builder. Consulte con el contacto de soporte técnico*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en la herramienta QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
