---
title: '"Parche de MDVA-29959: los administradores con permisos de "Clientes" no pueden administrar la cuenta de la empresa"'
description: El parche MDVA-29959 disponible en la herramienta [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) versión 1.0.5 corrige el problema en el que un usuario administrador restringido con todos los permisos para "Cliente" ACL no puede administrar compañías (añadir o eliminar una compañía). Tenga en cuenta que el problema se corrige en B2B para Adobe Commerce 2.3.4.
exl-id: ee246380-d37e-4c24-8435-97ae80088227
feature: Admin Workspace, B2B, Companies, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Parche de MDVA-29959: los administradores con permisos de &quot;Clientes&quot; no pueden administrar la cuenta de la empresa

El parche MDVA-29959 disponible en la herramienta [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) versión 1.0.5 corrige el problema en el que un usuario administrador restringido con todos los permisos para &quot;Cliente&quot; ACL no puede administrar compañías (agregar o eliminar una compañía). Tenga en cuenta que el problema se corrige en B2B para Adobe Commerce 2.3.4.

## Productos y versiones afectados

B2B para Adobe Commerce en la infraestructura en la nube 2.3.0-2.3.3-p1.

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario administrador con todos los permisos para &quot;Cliente&quot; ACL no puede administrar compañías (agregar o eliminar una compañía).

<u>Pasos a seguir</u>

1. En el Administrador de Commerce, cree un nuevo rol de administrador y asigne un usuario a ese rol.
1. Asigne únicamente recursos de &quot;Cliente&quot; a la función.
1. Inicie sesión como un usuario con esta función.
1. Intente eliminar una cuenta de compañía.

<u>Resultado esperado:</u>

La cuenta de empresa se ha eliminado correctamente.

<u>Resultado real:</u>

No puede eliminar la cuenta de la empresa. Obtienes *Lo sentimos, necesitas permisos para ver este contenido.* mensaje de error.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
