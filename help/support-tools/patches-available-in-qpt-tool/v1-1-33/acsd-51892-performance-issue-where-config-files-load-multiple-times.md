---
title: "ACSD-51892: Problema de rendimiento donde los archivos de configuración se cargan varias veces"
description: Aplique el parche ACSD-51892 para solucionar el problema de rendimiento de Adobe Commerce, donde los archivos de configuración se cargan varias veces durante la implementación.
feature: Observability
role: Admin
exl-id: 397343df-360f-43c4-bcef-be5f0da5aeef
source-git-commit: 97734799a39f41d0d6441379e21608fa5fcd1d4c
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-51892: Problema de rendimiento donde los archivos de configuración se cargan varias veces

El parche ACSD-51892 corrige el problema de rendimiento que se produce al cargar el `app/etc/env.php` y `app/etc/config.php` cada vez que se accede a los valores de configuración de implementación dentro de una sola solicitud. La lectura excesiva de archivos ejerce una presión sobre el sistema, lo que provoca un deterioro en el rendimiento general. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.33 está instalado. El ID del parche es ACSD-51892. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.6-p2.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Hay un problema de rendimiento en el que los archivos de configuración se cargan varias veces.

<u>Pasos a seguir</u>:

1. Realice la implementación o actualización a Adobe Commerce 2.4.6 o posterior.
1. Compruebe los registros del sistema de archivos para acceder a `app/etc/env.php` y `app/etc/config.php` archivos mientras se ejecuta la implementación.

<u>Resultados esperados</u>:

La implementación se realiza correctamente dentro del marco de tiempo normal.

<u>Resultados reales</u>:

* Los servidores tienen dificultades para responder a cualquier comando que introduzca. Esto resulta en *Error 503: tiempo de espera del primer byte* al acceder al sitio web.
* Hay varias entradas en los archivos de registro con acceso a `app/etc/env.php` y `app/etc/config.php` archivos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
