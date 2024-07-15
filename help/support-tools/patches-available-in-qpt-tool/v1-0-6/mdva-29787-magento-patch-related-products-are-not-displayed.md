---
title: "MDVA-29787: no se muestran los productos relacionados"
description: El parche MDVA-29787 resuelve el problema de que **Productos relacionados** no se muestren en un front-end de tienda Adobe Commerce. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6. El ID del parche es MDVA-29787.
exl-id: ee060d7b-3b0e-4bd5-84e6-fbd6d2fa532f
feature: Cache, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---

# MDVA-29787: no se muestran los productos relacionados

El parche MDVA-29787 resuelve el problema en el cual **Productos relacionados** no se muestran en un front-end de tienda Adobe Commerce. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6. El ID del parche es MDVA-29787.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce en la infraestructura en la nube 2.3.3.

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.0.

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La regla de destino para **Productos relacionados** no funciona cuando se usa la condición &quot;*es uno de*&quot; para que **Productos se muestren** en el administrador de Commerce.

>[!NOTE]
>
>Nota: Este parche no corrige las reglas de destino existentes. Debe volver a crear las reglas de destino existentes.

<u>Pasos a seguir</u>:

1. Crear **Nuevo Atributo** (Ejemplo: Test\_Attr).
   * Establecer tipo de entrada de catálogo **para el propietario de la tienda** = *Texto.*
   * En **Propiedades de tienda**, establezca **Usar para condiciones de regla de promoción** = *Sí*.
1. Crear **Nuevo Conjunto De Atributos** (Ejemplo: Test\_Set).
1. Agregue **Nuevo atributo** al **Nuevo conjunto de atributos** (Ejemplo: Agregue el atributo &quot;Test\_Attr&quot; al conjunto de atributos &quot;Test\_Set&quot;).
1. Cree tres productos. Para el ejemplo, se establecen de esta manera:
   * Product1, Test\_Attr = MAGT2NA\_Test3
   * Product2, Test\_Attr = 24-MB02
   * Product3, Test\_Attr = 701644329389M
1. Crear destino **Regla** (**Marketing**   > **Reglas de producto relacionadas** y haga clic en el botón **Agregar regla**.) con configuración:
   * **Aplicar A** = *Productos Relacionados*
   * **Productos que coinciden**
   * Establezca el nuevo atributo que creó **en** **Paso 1 anterior** como el atributo de Product1 (Ejemplo: Test\_Attr = MAGT2NA\_Test3).
   * **Productos para mostrar** = Los atributos de los otros dos productos (Ejemplo: atributos 24-MB02 y 701644329389M).
1. Guarde la **regla**.
1. Ejecute un reindexado, si es necesario.
1. Borrar caché.
1. Abra Product1 en el front-end.

<u>Resultados esperados</u>:

Los productos relacionados están presentes.

<u>Resultados reales</u>:

Faltan los productos relacionados.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
