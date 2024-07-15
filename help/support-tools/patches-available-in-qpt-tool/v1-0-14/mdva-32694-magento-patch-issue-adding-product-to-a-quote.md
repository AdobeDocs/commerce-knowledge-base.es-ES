---
title: "parche de MDVA-32694: problema al añadir un producto a un presupuesto"
description: El parche MDVA-32694 resuelve el problema de no poder agregar un producto válido en Administración a una cotización negociable creada en el sitio web no predeterminado.
exl-id: 964abbbd-c8b1-4645-a393-7283f52e94ff
feature: Products, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# parche de MDVA-32694: problema al añadir un producto a una cotización

El parche MDVA-32694 resuelve el problema de no poder agregar un producto válido en Administración a una cotización negociable creada en el sitio web no predeterminado.

Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce en la infraestructura en la nube 2.3.2 con B2B versión 1.2

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce en la infraestructura en la nube y Adobe Commerce local 2.3.0: 2.3.5-p2, 2.4.0, 2.4.1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Requisitos previos</u>:

Instale una nueva instancia de Adobe Commerce con B2B.

<u>Pasos a seguir</u>:

1. Vaya a **TIENDAS > Configuración > GENERAL > Características B2B** y habilite **Compañía** y **Presupuesto B2B**.
1. Cree 2 sitios web más con **tiendas** y **storeviews** (en total debería tener 3 sitios web: *base*, *sitio web2*, *sitio web3*).
1. Cree un producto simple y asígnelo solamente a *sitio web3*.
1. Vaya a **TIENDAS > Todas las tiendas** y establezca *sitio web3* como **predeterminado**.
1. Vaya al front-end y cree una nueva compañía en *sitio web3*.
1. Agregue el producto creado anteriormente al carro de compras y cree un nuevo presupuesto negociable.
1. Vaya a **TIENDAS > Todas las tiendas** y vuelva a establecer el sitio web &quot;*base*&quot; como **predeterminado**.
1. Vaya a **VENTAS > Ofertas > Abrir oferta creada anteriormente** e intente agregarle el mismo producto.

<u>Resultados esperados</u>:

El usuario administrador puede añadir el mismo producto a la cotización, según lo esperado.

<u>Resultados reales</u>:

El usuario administrador no puede añadir el mismo producto al presupuesto y aparece este mensaje de error:

```php
This product is assigned to another website.
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
