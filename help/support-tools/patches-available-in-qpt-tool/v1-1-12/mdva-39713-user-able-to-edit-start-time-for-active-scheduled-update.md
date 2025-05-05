---
title: "MDVA-39713: el usuario puede editar la hora de inicio de la actualización programada activa"
description: El parche de MDVA-39713 soluciona el problema en el que un usuario puede editar la hora de inicio de una actualización programada activa. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. El ID del parche es MDVA-39713. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: c7221fdb-5fc0-4179-8d4c-c9e1f0d00692
feature: CMS
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-39713: el usuario puede editar la hora de inicio de la actualización programada activa

El parche de MDVA-39713 soluciona el problema en el que un usuario puede editar la hora de inicio de una actualización programada activa. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. El ID del parche es MDVA-39713. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.3.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario puede editar la hora de inicio de una actualización programada activa.

<u>Pasos a seguir</u>:

1. Cree nuevas páginas de CMS.
1. Seleccione **Programar nueva actualización** y establezca la **fecha de inicio** en el minuto actual +1.
1. Active la Actualización programada ejecutando el comando `bin/magento cron:run --group=staging` en el entorno local. Espere unos minutos y compruebe si la programación está activa.
1. Una vez activada la programación, actualice la página.
1. Haga clic en **Ver/Editar** en la sección Cambios programados.
1. Edite el tiempo añadiendo +2 minutos y guarde el cambio.
1. Guarde la página de CMS.
1. De nuevo, ejecute el siguiente comando: `bin/magento cron:run --group=staging`.
1. Haga clic en **Ver/Editar** de la actualización programada.

<u>Resultados esperados</u>:

El usuario no puede editar la hora de inicio de una actualización programada activa.

<u>Resultados reales</u>:

El usuario recibe un error como *Item (Magento\Cms\Model\Page) con el mismo ID &quot;11&quot; ya existe.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/usage) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en nuestra documentación para desarrolladores.
