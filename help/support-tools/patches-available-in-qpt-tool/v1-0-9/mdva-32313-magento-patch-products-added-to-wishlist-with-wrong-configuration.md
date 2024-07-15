---
title: "Parche MDVA-32313: productos añadidos a la lista de deseos con una configuración incorrecta"
description: El parche MDVA-32313 resuelve el problema en el que los productos configurables no se pueden añadir correctamente a la lista de deseos, porque se les asignan configuraciones incorrectas cuando se añaden a la lista de deseos. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10. Tenga en cuenta que el problema se corrigió en la versión 2.4.2 de Adobe Commerce.
exl-id: e7ac5ef5-1389-4108-b2bc-73d43eb3e7ca
feature: Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# Parche MDVA-32313: productos añadidos a la lista de deseos con una configuración incorrecta

El parche MDVA-32313 resuelve el problema en el que los productos configurables no se pueden añadir correctamente a la lista de deseos, porque se les asignan configuraciones incorrectas cuando se añaden a la lista de deseos. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10. Tenga en cuenta que el problema se corrigió en la versión 2.4.2 de Adobe Commerce.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.0

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.0 - 2.3.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir</u>:

1. Crear un cliente.
1. Inicie sesión en la cuenta de cliente.
1. Vaya a la página **Lista de productos**.
1. Elija un producto configurable (Ejemplo: *configurable\_1* ) y seleccione las opciones de tamaño y color preferidos en la página **Lista de productos** (**No abra la página del producto.**).
1. Haga clic en el icono de la lista de deseos de otro producto configurable (Ejemplo: *configurable\_2*) en la misma página sin seleccionar ninguna opción de color o tamaño.

<u>Resultados esperados</u>:

El producto *configurable\_2* se agrega a la lista de deseos sin las opciones seleccionadas, como se espera.

<u>Resultados reales</u>:

El producto *configurable\_2* se agregó a la lista de deseos con la configuración del producto *configurable\_1*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
