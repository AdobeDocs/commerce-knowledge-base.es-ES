---
title: "MDVA-28661: problema con la administración de usuarios de la empresa al cambiar el correo electrónico de administración"
description: El parche MDVA-28861 corrige el problema en el que los usuarios reciben un error al cambiar el correo electrónico del administrador. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5. El ID del parche es MDVA-28861.
exl-id: 2d6691e5-baaf-4cef-ae7e-2b6ccc7f2cd3
feature: Admin Workspace, Communications, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-28661: problema con la administración de usuarios de la empresa al cambiar el correo electrónico de administración

El parche MDVA-28861 corrige el problema en el que los usuarios reciben un error al cambiar el correo electrónico del administrador. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5. El ID del parche es MDVA-28861.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.0 a 2.4.1 (incluida 2.3.5-p1) con extensión B2B

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Después de cambiar la dirección de correo electrónico **Administrador de la compañía**, se devuelve un error y no se muestra la lista **Usuarios de la compañía**.

<u>Pasos a seguir</u>:

1. Habilite la funcionalidad Compañía (obtenga más información sobre esto en [Instalar B2B: habilite las características B2B en el administrador de Commerce](https://devdocs.magento.com/extensions/b2b/#enable-b2b-features-in-magento-admin) en nuestra documentación para desarrolladores y cree una nueva Compañía con dos usuarios (un administrador y dos usuarios) y todos con direcciones de correo electrónico).
1. Vaya a **Commerce Admin** > **Clientes** > **Compañías** y abra su cuenta de Compañía.
1. Abra la pestaña **Administrador de la compañía** y cambie el administrador al primer usuario, lo que incluye cambiar el correo electrónico de **Administrador de la compañía** al primer correo electrónico del usuario.
1. Vaya al front-end de Adobe Commerce e inicie sesión como el primer usuario.
1. Vaya a la sección **Usuarios de la compañía**.

<u>Resultados esperados</u>:

La lista **Usuarios de la compañía** debe mostrarse según lo esperado.

<u>Resultados reales</u>:

No se muestra la lista **Usuarios de la compañía** y se muestra un error similar al siguiente:

```bash
No such entity with id = 2
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.

Para obtener más información sobre la funcionalidad de B2B Company, consulte estos artículos en nuestra documentación para desarrolladores:

* [Guía para desarrolladores B2B](https://devdocs.magento.com/guides/v2.4/b2b/bk-b2b.html)
* [Administrar roles de compañía](https://devdocs.magento.com/guides/v2.4/b2b/roles.html)
* [Referencia de rutas de configuración de la extensión Adobe Commerce Enterprise B2B](https://devdocs.magento.com/guides/v2.4/config-guide/prod/config-reference-b2b.html)
