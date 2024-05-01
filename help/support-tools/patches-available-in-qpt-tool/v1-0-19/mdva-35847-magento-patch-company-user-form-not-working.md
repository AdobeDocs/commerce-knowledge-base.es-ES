---
title: "MDVA-35847: El formulario de usuario de la empresa no funciona"
description: El parche MDVA-35847 soluciona el problema de que el formulario de usuario de la empresa no funciona y devuelve un error 500 en el front-end. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. El ID del parche es MDVA-35847. Tenga en cuenta que el problema se corrigió en la versión 2.4.3 de Adobe Commerce.
exl-id: 1a3f4a61-0c21-460a-ae48-e792d03ed805
feature: B2B, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# MDVA-35847: El formulario de usuario de la empresa no funciona

El parche MDVA-35847 soluciona el problema de que el formulario de usuario de la empresa no funciona y devuelve un error 500 en el front-end. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 está instalado. El ID del parche es MDVA-35847. Tenga en cuenta que el problema se corrigió en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.4.2

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.1-2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Requisitos previos</u>:

Adobe Commerce B2B está instalado.

<u>Pasos a seguir</u>:

1. Ir a **Tiendas** > **Atributos** > **Cliente** y cree un nuevo atributo de cliente personalizado:

   * Tipo de entrada = *Fecha*
   * Mostrar en tienda = *Sí*
   * Orden de clasificación = *0*
   * Forms para usar en = *Todos los formularios*

1. Cree una nueva compañía.
1. Inicie sesión como administrador de empresa en el front-end.
1. Vaya a las secciones Usuarios de la empresa.

<u>Resultados esperados</u>:

El formulario Usuario de empresa se carga normalmente.

<u>Resultados reales</u>:

El formulario Usuario de empresa no se carga y devuelve un error 500.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
