---
title: "MDVA-41164: No se puede guardar ni editar la compañía con atributos de cliente personalizados"
description: El parche MDVA-41164 resuelve el problema en el que el usuario administrador no puede guardar o editar una empresa con atributos de cliente personalizados de archivos o imágenes de cualquier tipo. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5. El ID del parche es MDVA-41164. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: 24338895-68b4-404c-bedd-46cfc7e983a0
feature: Admin Workspace, Attributes, B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-41164: No se puede guardar ni editar la compañía con atributos de cliente personalizados

El parche MDVA-41164 resuelve el problema en el que el usuario administrador no puede guardar o editar una empresa con atributos de cliente personalizados de archivos o imágenes de cualquier tipo. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 está instalado. El ID del parche es MDVA-41164. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario administrador no puede guardar ni editar una empresa con atributos de cliente personalizados de archivos o imágenes de cualquier tipo.

<u>Requisitos previos</u>:

El módulo B2B está instalado.

<u>Pasos a seguir</u>:

1. Habilitar compañía en **Tiendas** > **Configuración** > **Funciones B2B**.
1. Crear un atributo de cliente en **Tiendas** > **Atributos** > **Clientes** > **Añadir nuevo atributo**:
   * Tipo de entrada: Archivo (adjunto)
   * Mostrar en la tienda: Sí
   * Orden de clasificación: Cualquiera
   * Forms que se usará en: seleccionar todo
1. Cree una nueva compañía en **Clientes** > **Compañías** > **Añadir nueva compañía** y cargue un archivo para el nuevo atributo creado anteriormente.

<u>Resultados esperados</u>:

El usuario puede completar la creación de la empresa y el archivo adjunto se carga sin ningún error.

<u>Resultados reales</u>:

* Aparece un mensaje de error: *Se ha producido un error al guardar el archivo.*
* El registro de excepciones contiene un registro como el siguiente:

  ```php
  report.CRITICAL: Notice: Undefined index: customer in
  ../app/code/Magento/Customer/Controller/Adminhtml/File/Customer/Upload.php on line 69
  ```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sección.
