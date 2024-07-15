---
title: "Parche de MDVA-32739: correos electrónicos antiguos enviados cuando el envío asincrónico está habilitado"
description: El parche de MDVA-32739 soluciona el problema que causaba que, al habilitar [notificaciones de correo electrónico asincrónicas](https://devdocs.magento.com/guides/v2.4/performance-best-practices/configuration.html#asynchronous-email-notifications), se enviaran correos electrónicos de ventas antiguos. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.2.
exl-id: 8cf4ef8a-f2f2-47fb-9f69-0eedcc10ba8b
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# Parche MDVA-32739: correos electrónicos antiguos enviados cuando el envío asincrónico está habilitado

El parche MDVA-32739 soluciona el problema que causaba que habilitar [notificaciones asincrónicas por correo electrónico](https://devdocs.magento.com/guides/v2.4/performance-best-practices/configuration.html#asynchronous-email-notifications) enviara correos electrónicos de ventas antiguos. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.5-p2

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.0 - 2.4.1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir</u>:

1. Deshabilite el envío asincrónico de correo electrónico.
1. Cree un pedido y asegúrese de que el envío del correo electrónico esté fallando.
1. Habilite el envío asincrónico.

<u>Resultados esperados</u>:

Los correos electrónicos se envían únicamente para los pedidos, envíos, facturas y notas de abono que se crearon después de la última actualización de envío asincrónica.

<u>Resultados reales</u>:

El correo electrónico antiguo se enviará mediante el cronjob.

## Fix

Con la corrección incluida en el parche, Adobe Commerce selecciona los pedidos que se crean después de que se haya ejecutado por última vez el método de envío asincrónico y envía el correo electrónico correspondiente a dichos pedidos.

De forma predeterminada, se selecciona con un desplazamiento de -1 día.

Puede cambiar este valor (a -2 días por ejemplo) modificando `di.xml`.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
