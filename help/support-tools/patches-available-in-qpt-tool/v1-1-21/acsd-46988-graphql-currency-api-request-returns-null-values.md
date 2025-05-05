---
title: "ACSD-46988: La solicitud de API de divisa de GraphQL devuelve valores nulos"
description: El parche ACSD-46988 corrige el problema en el que la solicitud de API de GraphQL currency devuelve valores nulos para una moneda personalizada. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21. El ID del parche es ACSD-46988. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.
exl-id: 8da0ab99-8db9-4222-9400-6df1520267f0
feature: REST, GraphQL
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-46988: La solicitud de API de divisa de GraphQL devuelve valores nulos

El parche ACSD-46988 corrige el problema en el que la solicitud de API de GraphQL currency devuelve valores nulos para una moneda personalizada. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21. El ID del parche es ACSD-46988. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La solicitud de API de GraphQL currency devuelve valores nulos para una moneda personalizada.

<u>Pasos a seguir</u>:

1. Configure la moneda personalizada en el Administrador. Vaya a **Sistema** > **Configuración** > **General** > **Configuración de moneda**.
1. Envíe una solicitud de GraphQL con la siguiente carga útil:

<pre>
<code class="language-graphql">
&lbrace;
    currency &lbrace;
        base_currency_code
        base_currency_symbol
        default_display_currency_code
        default_display_currency_symbol
        available_currency_codes
        exchange_rates &lbrace;
            currency_to
            rate
        &rbrace;
    &rbrace;
&rbrace;
</code>
</pre>

<u>Resultados esperados</u>:

La solicitud devuelve valores de moneda en lugar de valores nulos.

<u>Resultados reales</u>:

La solicitud devuelve varios valores nulos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Herramientas de parches de calidad > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía de la herramienta de parches de calidad.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Pasos adicionales necesarios tras la instalación del parche

Para usuarios locales:

* Ejecutar: `composer require symfony/intl:"~5.4.11"`

Para usuarios de Cloud:

* Ejecutar: `composer require symfony/intl:"~5.4.11"`
* Inserte `composer.json` y `composer.lock` archivos en el repositorio de Git junto con el archivo de revisión.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información acerca de otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía Herramienta de parches de calidad.
