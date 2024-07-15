---
title: "MDVA-31343 patch: la actualización de la programación elimina la clase principal de la categoría"
description: El parche MDVA-31343 corrige el problema en el que la clase CSS del cuerpo de diseño asignada para una categoría se elimina durante la actualización programada. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Se ha programado la corrección del problema en Adobe Commerce 2.4.2.
exl-id: 50dbff01-cb77-4cac-b90e-5c4b06f5e4e7
feature: Cache, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# Revisión de MDVA-31343: la actualización de programación elimina la clase de cuerpo para la categoría

El parche MDVA-31343 corrige el problema en el que la clase CSS del cuerpo de diseño asignada para una categoría se elimina durante la actualización programada. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Se ha programado la corrección del problema en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.5-p2

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La clase de cuerpo de diseño se elimina de la categoría después de la actualización programada.

<u>Pasos a seguir</u>:

1. En el Administrador de Commerce, cree una categoría.
1. Definir **diseño** = *categoría — ancho completo* en la sección **Diseño**.
1. Guarde la categoría.
1. Vaya a la página de front-end de categoría. En el origen de la página, observe lo siguiente

   ```css
   page-layout-category-full-width
   ```

   Clase CSS.
1. En **CATÁLOGO** > **Categoría**, haga clic en **Programar nueva actualización** en la sección *Cambios programados* para la nueva categoría.
1. Espere a que se inicie la actualización programada, ejecute cron y vacíe la caché.
1. Vaya a la página de categoría en el front-end e inspeccione el origen de la página.

<u>Resultados esperados</u>:

En el cuerpo de la página, verá el

```css
page-layout-category-full-width
```

Clase CSS.

<u>Resultados reales</u>:

En el cuerpo de la página, verá el

```css
page-layout-2columns-left
```

Clase CSS, que es la predeterminada para la página de categoría.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
