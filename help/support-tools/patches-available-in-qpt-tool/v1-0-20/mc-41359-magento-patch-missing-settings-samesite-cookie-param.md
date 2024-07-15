---
title: "Parche de comercio MC-41359: falta el parámetro de cookie SameSite de la configuración"
description: El parche de comercio MC-41359 corrige el problema con la configuración de parámetros de cookie SameSite que falta. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. El ID del parche es MC-41359. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.
exl-id: b48faa3f-0d9a-4d65-9abb-1573c6240635
feature: Observability
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Parche de comercio MC-41359: falta el parámetro de cookie SameSite de configuración

El parche de comercio MC-41359 corrige el problema con la configuración de parámetros de cookie SameSite que falta. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. El ID del parche es MC-41359. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:** Adobe Commerce en la infraestructura en la nube 2.4.2

**Compatible con versiones de Adobe Commerce:** Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.6-p1, 2.4.2, 2.4.2-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Falta la configuración del parámetro de cookie SameSite.

<u>Pasos a seguir:</u>

Requisitos previos:

* Abra Chrome y vaya a chrome://flags/
* Habilitar **SameSite con cookies predeterminadas** y **Las cookies sin SameSite debe ser seguras**.
* Abra el inspector de Chrome.

<u>Escenario 1:</u>

1. Activar PayPal.
1. Ve a la tienda.
1. Añadir un producto al carro de compras.
1. Vaya a Pago y envío.

<u>Escenario 2:</u>

Si tiene New Relic [habilitado](https://docs.magento.com/user-guide/reports/new-relic-reporting.html), la advertencia aparecerá en cualquier página de front-end.

<u>Resultado real:</u>

Mensaje de advertencia en la consola del explorador: *Se estableció una cookie asociada a un recurso entre sitios sin un atributo SameSite.*

<u>Resultado esperado:</u>

no se debe agregar &quot;lax&quot; al dominio de la cookie; el atributo samesite debe estar presente con el valor predeterminado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obtener información sobre otros parches disponibles en la herramienta QPT, consulte [Parches disponibles en la herramienta QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
