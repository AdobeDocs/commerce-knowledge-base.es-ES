---
title: "MDVA-29042: permisos de categoría global sin cambios"
description: El parche de MDVA-29042 corrige el problema en el que los permisos de catálogo se cambiaban a "*Permitir*" automáticamente después de que se añadiera un nuevo producto al catálogo compartido en el administrador de Commerce. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.3.6 con la extensión B2B.
exl-id: 491b8881-87ec-4820-8f87-54961682e961
feature: Catalog Management, Categories, Customer Service, Roles/Permissions
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# MDVA-29042: permisos de categoría global sin cambios

La revisión MDVA-29042 corrige el problema en el cual los permisos de catálogo se cambiaban a &quot;*Permitir*&quot; automáticamente después de que se agregara un nuevo producto al catálogo compartido en el administrador de Commerce. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.3.6 con la extensión B2B.

## Productos y versiones afectados

Adobe Commerce (todos los métodos de implementación) 2.3.3 a 2.3.4-p2 con extensión B2B

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al anular la selección de un grupo de clientes de los permisos de categoría global en el administrador de Commerce, no se establece automáticamente ese grupo de clientes en &quot;*Denegar*&quot; dentro de los permisos de categoría.

<u>Requisitos previos</u>:

* Instancia B2B con un grupo de clientes definido y seleccionado en **TIENDAS** > **Configuración** > **CATÁLOGO** > **Catálogo** > **Permisos de categoría** para:
   * **Permitir categoría de exploración**
   * **Mostrar precios de productos**
   * **Permitir la adición al carro**
* En cada **categoría**, el grupo de clientes se define como &quot;*Permitir*&quot; para:
   * **Categoría de exploración**
   * **Mostrar precios de productos**
   * **Agregar al carro**

<u>Pasos a seguir</u>:

1. En el Administrador de Commerce, vaya a **TIENDAS** > **Configuración** > **CATÁLOGO** > **Catálogo** > **Permisos de categoría** y anule la selección del grupo de clientes de:
   * **Permitir categoría de exploración**
   * **Mostrar precios de productos**
   * **Permitir la adición al carro**
1. Haga clic en el botón **Guardar configuración**.
1. Espere a que se ejecuten los indexadores.
1. Consulte **CATÁLOGO** > **Categorías** > **Permisos de categoría**.

<u>Resultados esperados</u>:

**Permisos de categoría** se establecerá en &quot;*Denegar*&quot; para todas las categorías del grupo de clientes.

<u>Resultados reales</u>:

Sin cambios en los permisos de categoría para el grupo de clientes.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.

Para obtener más información sobre la funcionalidad de la compañía B2B, consulte los siguientes artículos en nuestra documentación para desarrolladores:

* [Guía para desarrolladores B2B](https://devdocs.magento.com/guides/v2.4/b2b/bk-b2b.html)
* [Administrar roles de compañía](https://devdocs.magento.com/guides/v2.4/b2b/roles.html)
* [Referencia de rutas de configuración de la extensión Adobe Commerce Enterprise B2B](https://devdocs.magento.com/guides/v2.4/config-guide/prod/config-reference-b2b.html)
