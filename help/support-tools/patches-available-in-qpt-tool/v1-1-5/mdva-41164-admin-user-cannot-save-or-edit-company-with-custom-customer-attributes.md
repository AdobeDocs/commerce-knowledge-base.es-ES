---
title: "MDVA-41164: No se puede guardar ni editar la compañía con atributos de cliente personalizados"
description: El parche MDVA-41164 resuelve el problema en el que el usuario administrador no puede guardar o editar una empresa con atributos de cliente personalizados de archivos o imágenes de cualquier tipo. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5. El ID del parche es MDVA-41164. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: 24338895-68b4-404c-bedd-46cfc7e983a0
feature: Admin Workspace, Attributes, B2B, Companies
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-41164: No se puede guardar ni editar la compañía con atributos de cliente personalizados

El parche MDVA-41164 resuelve el problema en el que el usuario administrador no puede guardar o editar una empresa con atributos de cliente personalizados de archivos o imágenes de cualquier tipo. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5. El ID del parche es MDVA-41164. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario administrador no puede guardar ni editar una empresa con atributos de cliente personalizados de archivos o imágenes de cualquier tipo.

<u>Requisitos previos</u>:

El módulo B2B está instalado.

<u>Pasos a seguir</u>:

1. Habilitar la compañía en **tiendas** > **configuración** > **características B2B**.
1. Crear un atributo de cliente en **Tiendas** > **Atributos** > **Clientes** > **Agregar nuevo atributo**:
   * Tipo de entrada: Archivo (adjunto)
   * Mostrar en la tienda: Sí
   * Orden de clasificación: Cualquiera
   * Forms que se usará en: seleccionar todo
1. Cree una nueva compañía en **Clientes** > **Compañías** > **Agregar nueva compañía** y cargue un archivo para el nuevo atributo creado anteriormente.

<u>Resultados esperados</u>:

El usuario puede completar la creación de la empresa y el archivo adjunto se carga sin ningún error.

<u>Resultados reales</u>:

* Aparece un mensaje de error: *Se produjo un error al guardar el archivo.*
* El registro de excepciones contiene un registro como el siguiente:

  ```php
  report.CRITICAL: Notice: Undefined index: customer in
  ../app/code/Magento/Customer/Controller/Adminhtml/File/Customer/Upload.php on line 69
  ```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
