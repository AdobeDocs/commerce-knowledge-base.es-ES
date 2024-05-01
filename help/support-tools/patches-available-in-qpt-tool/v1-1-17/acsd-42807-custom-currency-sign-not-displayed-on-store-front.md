---
title: "ACSD-42807: El signo de moneda personalizado no se muestra en la tienda"
description: El parche de ACSD-42807 corrige el problema en el que el signo de moneda personalizado no se muestra en la tienda. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17. El ID del parche es ACSD-42807. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.
exl-id: 21bd17b4-d9d8-4c40-8f89-d6f7b930b475
feature: Storefront
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-42807: el signo de moneda personalizado no se muestra en la tienda

El parche de ACSD-42807 corrige el problema en el que el signo de moneda personalizado no se muestra en la tienda. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 está instalado. El ID del parche es ACSD-42807. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El signo de moneda personalizado no se muestra en la tienda.

<u>Pasos a seguir</u>:

1. Ir a **Almacenar** > **Configuración** > **Configuraciones** > **General** > **Configuración de moneda** y seleccione cualquier moneda personalizada. Por ejemplo,. **Peso mexicano**.
1. Ir a **Almacenar** > **Configuración** > **Configuraciones** > **General** > **Opciones de configuración regional** y seleccione **Español (México)**.
1. Ir a **Almacenar** > **Símbolos de moneda** y configure el símbolo de moneda en **MX$**.
1. Compruebe el símbolo de moneda en el front-end.

<u>Resultados esperados</u>:

El símbolo de moneda predeterminado es &quot;MX$&quot;, con la moneda establecida como &quot;Peso mexicano&quot; y la configuración regional establecida como &quot;Español (México)&quot;.

<u>Resultados reales</u>:

El símbolo de moneda predeterminado muestra &quot;$&quot;.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
