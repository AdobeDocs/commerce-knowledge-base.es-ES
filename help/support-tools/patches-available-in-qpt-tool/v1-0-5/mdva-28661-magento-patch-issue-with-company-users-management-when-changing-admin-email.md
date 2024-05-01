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

El parche MDVA-28861 corrige el problema en el que los usuarios reciben un error al cambiar el correo electrónico del administrador. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 está instalado. El ID del parche es MDVA-28861.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.0 a 2.4.1 (incluida 2.3.5-p1) con extensión B2B

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Después de cambiar el **Administrador de empresa** dirección de correo electrónico, se devuelve un error y la variable **Usuarios de empresa** no se muestra la lista.

<u>Pasos a seguir</u>:

1. Habilite la funcionalidad Compañía (Obtenga más información sobre esto en [Instalación de B2B: Habilitar funciones B2B en el administrador de Commerce](https://devdocs.magento.com/extensions/b2b/#enable-b2b-features-in-magento-admin) en nuestra documentación para desarrolladores y cree una nueva compañía con dos usuarios (un administrador y dos usuarios) (todos con direcciones de correo electrónico).
1. Vaya a la **Administrador de Commerce** > **Clientes** > **Compañías** y abra su Cuenta de compañía.
1. Abrir **Administrador de empresa** y cambie admin al primer usuario, lo que incluye cambiar el **Administrador de empresa** correo electrónico al correo electrónico del primer usuario.
1. Vaya al front-end de Adobe Commerce e inicie sesión como el primer usuario.
1. Vaya a la **Usuarios de empresa** sección.

<u>Resultados esperados</u>:

El **Usuarios de empresa** La lista debe mostrarse según lo esperado.

<u>Resultados reales</u>:

El **Usuarios de empresa** no se muestra y aparece un error similar al siguiente:

```bash
No such entity with id = 2
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.

Para obtener más información sobre la funcionalidad de B2B Company, consulte estos artículos en nuestra documentación para desarrolladores:

* [Guía para desarrolladores de B2B](https://devdocs.magento.com/guides/v2.4/b2b/bk-b2b.html)
* [Administrar funciones de empresa](https://devdocs.magento.com/guides/v2.4/b2b/roles.html)
* [Referencia de rutas de configuración de la extensión Adobe Commerce Enterprise B2B](https://devdocs.magento.com/guides/v2.4/config-guide/prod/config-reference-b2b.html)
