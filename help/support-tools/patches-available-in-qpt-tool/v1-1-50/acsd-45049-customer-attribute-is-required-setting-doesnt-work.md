---
title: "ACSD-45049: La configuración de atributos 'Es obligatorio' del cliente no funciona según el ámbito del sitio web en Administración"
description: Aplique el parche ACSD-45049 para corregir el problema de Adobe Commerce en el que el atributo del cliente "[!UICONTROL Is required]" no se ha anulado correctamente según el ámbito del sitio web en Administración.
feature: Attributes, Customers
role: Admin, Developer
source-git-commit: 16e7c9e4e4bbbc62db0671016bce85ecb6414622
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-45049: la configuración de atributos del cliente *[!UICONTROL Is required]* no funciona según el ámbito del sitio web en el administrador

El parche ACSD-45049 corrige el problema en el que la configuración de atributos del cliente *[!UICONTROL Is required]* no funciona correctamente según el ámbito del sitio web en Administración. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.50. El ID del parche es ACSD-45049. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.4-p7 y 2.4.5 - 2.4.5-p9

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La configuración del atributo *[!UICONTROL Is required]* del cliente no funciona correctamente según el ámbito del sitio web en Administración.

<u>Pasos a seguir</u>:

1. Cree dos sitios web.
1. Abra **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer attribute]**.
1. Crear un nuevo atributo, establecer **[!UICONTROL Is value required]** = *No*.
1. Cambie al sitio web predeterminado y cambie **[!UICONTROL Is value required]** = *Sí*. El otro sitio web tiene el valor predeterminado.
1. Cree un nuevo cliente desde Administración para el sitio web no predeterminado.

<u>Resultados esperados</u>:

El atributo no es necesario para el sitio web no predeterminado.

<u>Resultados reales</u>:

* El atributo es necesario para el sitio web no predeterminado al crear un cliente en Administración.
* El atributo no es necesario para el sitio web no predeterminado al registrar un cliente en la tienda.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].