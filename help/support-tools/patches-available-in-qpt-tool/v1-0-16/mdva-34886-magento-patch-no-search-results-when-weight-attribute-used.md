---
title: '"MDVA-34886: no hay resultados de búsqueda cuando se utiliza el atributo "weight"'
description: El parche MDVA-34886 resuelve el problema de que la búsqueda no devuelve resultados cuando el atributo de peso se configura como en el que se puede buscar. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16. Tenga en cuenta que el problema se corrigió en la versión 2.4.3 de Adobe Commerce.
exl-id: e6f33772-0167-4a54-9d62-0ab89edb5d1d
feature: Attributes, Cache, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-34886: no hay resultados de búsqueda cuando se utiliza el atributo &quot;weight&quot;

El parche MDVA-34886 resuelve el problema de que la búsqueda no devuelve resultados cuando el atributo de peso se configura como en el que se puede buscar. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 está instalado. Tenga en cuenta que el problema se corrigió en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.5-p1

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.2 - 2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La búsqueda no devuelve resultados cuando el atributo de peso se configura como en el que se puede buscar.

<u>Pasos a seguir</u>:

1. Configure el Elasticsearch.
1. Vaya a **Administrador** > **Tiendas** > **Atributos** > **Product**. Edite el **Grosor** y establezca su atributo **Buscable** = *Sí*.
1. Guarde el atributo y borre la caché de configuración.
1. En el front-end, busque un valor de texto (ejemplo: *bolso*).
1. Observe que la búsqueda no devuelve ningún resultado.
1. El registro de excepciones contendrá un mensaje de error como:

```php
{"type":"number_format_exception","reason":"For input string: \"bag\""}
```

<u>Resultados esperados</u>:

La búsqueda devuelve resultados incluso cuando el atributo weight está configurado como en el que se puede buscar, según lo esperado.

<u>Resultados reales</u>:

La búsqueda no devuelve resultados cuando el atributo de peso se configura como en el que se puede buscar.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
