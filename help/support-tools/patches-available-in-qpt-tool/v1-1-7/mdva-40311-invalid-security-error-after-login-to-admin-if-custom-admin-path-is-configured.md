---
title: '"MDVA-40311: Error "Seguridad no válida o clave de formulario" después de iniciar sesión en el administrador si se ha configurado la ruta de administración personalizada"'
description: '''El parche de MDVA-40311 corrige el problema en el que el usuario administrador recibe un mensaje de error: *Seguridad o clave de formulario no válidas. Actualice la página*, después de iniciar sesión en el administrador, si la ruta de administración personalizada está configurada y la clave secreta está habilitada. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7. El ID del parche es MDVA-40311. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4."'
exl-id: d4562f09-0aed-438e-8c2e-90557aa2f146
feature: Admin Workspace, Compliance, Security
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-40311: Error &quot;Seguridad no válida o clave de formulario&quot; después de iniciar sesión en el administrador si se ha configurado la ruta de administración personalizada

El parche MDVA-40311 corrige el problema en el que el usuario administrador recibe un mensaje de error: *Clave de formulario o seguridad no válida. Actualice la página*, después de iniciar sesión en el administrador, si la ruta de administración personalizada está configurada y la clave secreta está habilitada. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7. El ID del parche es MDVA-40311. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario administrador recibe un mensaje de error: *Clave de formulario o seguridad no válida. Actualice la página*, después de iniciar sesión en el administrador, si la ruta de administración personalizada está configurada y la clave secreta está habilitada.

<u>Pasos a seguir</u>:

* Inicie sesión como el usuario administrador con un nombre de usuario y una contraseña válidos.

<u>Resultados esperados</u>:

El usuario puede iniciar sesión sin ningún mensaje de error.

<u>Resultados reales</u>:

*Clave de formulario o seguridad no válida. Actualice la página* si se muestra el mensaje de error.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
