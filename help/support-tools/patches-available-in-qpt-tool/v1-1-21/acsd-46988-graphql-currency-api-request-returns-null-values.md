---
title: "ACSD-46988: La solicitud de API de divisa de GraphQL devuelve valores nulos"
description: El parche ACSD-46988 corrige el problema en el que la solicitud de API de GraphQL currency devuelve valores nulos para una moneda personalizada. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21. El ID del parche es ACSD-46988. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.
exl-id: 8da0ab99-8db9-4222-9400-6df1520267f0
feature: REST, GraphQL
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-46988: La solicitud de API de divisa de GraphQL devuelve valores nulos

El parche ACSD-46988 corrige el problema en el que la solicitud de API de GraphQL currency devuelve valores nulos para una moneda personalizada. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 está instalado. El ID del parche es ACSD-46988. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.5

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La solicitud de API de GraphQL currency devuelve valores nulos para una moneda personalizada.

<u>Pasos a seguir</u>:

1. Configure la moneda personalizada en el Administrador. Ir a **Sistema** > **Configuración** > **General** > **Configuración de moneda**.
1. Envíe una solicitud de GraphQL con la siguiente carga útil:

<pre>
<code class="language-graphql">
{
    currency {
        base_currency_code
        base_currency_symbol
        default_display_currency_code
        default_display_currency_symbol
        available_currency_codes
        exchange_rates {
            currency_to
            rate
        }
    }
}
</code>
</pre>

<u>Resultados esperados</u>:

La solicitud devuelve valores de moneda en lugar de valores nulos.

<u>Resultados reales</u>:

La solicitud devuelve varios valores nulos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Parches de calidad > Herramientas > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía de la herramienta Parches de calidad.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Pasos adicionales necesarios tras la instalación del parche

Para usuarios locales:

* Ejecutar: `composer require symfony/intl:"~5.4.11"`

Para usuarios de Cloud:

* Ejecutar: `composer require symfony/intl:"~5.4.11"`
* Push `composer.json` y `composer.lock` al repositorio de git junto con el archivo de parche.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía de la herramienta Parches de calidad.
