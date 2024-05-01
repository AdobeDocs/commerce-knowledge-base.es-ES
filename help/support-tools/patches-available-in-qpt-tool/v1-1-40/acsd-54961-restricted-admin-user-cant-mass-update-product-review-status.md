---
title: "ACSD-54961: El usuario administrador restringido no puede realizar una actualización masiva [!UICONTROL Product Review status]"
description: Aplique el parche ACSD-54961 para corregir el problema de Adobe Commerce en el que un usuario administrador restringido no puede actualizar el estado de la revisión del producto de forma masiva.
feature: Products
role: Admin, Developer
exl-id: 26c5bacd-21de-4533-a7b6-4acbacd38fec
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-54961: el usuario administrador restringido no puede realizar una actualización masiva [!UICONTROL Product Review status]

El parche ACSD-54961 corrige el problema en el que un usuario administrador restringido no puede realizar una actualización masiva [!UICONTROL Product Review status]. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 está instalado. El ID del parche es ACSD-54961. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Un usuario administrador restringido no puede realizar una actualización masiva [!UICONTROL Product Review status].

<u>Pasos a seguir</u>:

1. Cree un sitio web, una tienda y una vista de tienda adicionales.
1. Agregue un producto a la segunda tienda y, a continuación, agregue una revisión.
1. Cree un usuario administrador restringido con acceso solo a la segunda tienda.
1. Inicie sesión como usuario administrador restringido y, a continuación, vaya a **[!UICONTROL  Marketings]** > **[!UICONTROL Reviews]** > **[!UICONTROL Mass Update]** y configure el **Estado** hasta *Aprobado* o *Pendiente*.

<u>Resultados esperados</u>:

El usuario administrador restringido puede actualizar las críticas mediante el **[!UICONTROL Mass Update]** acción.

<u>Resultados reales</u>:

Se produce un error al actualizar las revisiones mediante **[!UICONTROL Mass Update]** acción.<br>
El `var/log/exception.log` contiene un error similar:

```
report.CRITICAL: TypeError: array_intersect(): Argument #1 ($array) must be of type array, null given in app/code/Magento/AdminGws/Model/Models.php:439
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
