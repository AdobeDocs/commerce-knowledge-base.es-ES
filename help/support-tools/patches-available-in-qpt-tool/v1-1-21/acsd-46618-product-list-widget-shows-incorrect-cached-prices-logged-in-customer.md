---
title: "ACSD-46618: el widget de lista de productos muestra precios en caché incorrectos para clientes que iniciaron sesión"
description: Aplique un parche para corregir el problema de Adobe Commerce en el que el widget de lista de productos muestra precios en caché incorrectos para un cliente que ha iniciado sesión.
exl-id: 8b182822-1d3d-4793-871b-cdf4565d0712
feature: Cache, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-46618: el widget de lista de productos muestra precios en caché incorrectos para un cliente que ha iniciado sesión

El parche ACSD-46618 soluciona el problema de que el widget de lista de productos muestra precios en caché incorrectos para un cliente que ha iniciado sesión. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html?lang=es) 1.1.21. El ID del parche es ACSD-46618. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El parche ACSD-46618 soluciona el problema de que el widget de lista de productos muestra precios en caché incorrectos para un cliente que ha iniciado sesión.

<u>Pasos a seguir</u>:

1. En el Administrador de Adobe Commerce, seleccione **[!UICONTROL Stores]**, luego **[!UICONTROL Configuration]**, expanda **[!UICONTROL Sales]** y seleccione **[!UICONTROL Tax]**. Actualice la configuración de impuestos para mostrar los precios, incluidos y excluidos los impuestos.
1. Conjunto **[!UICONTROL Enable Cross Border Trade]** = _Sí_.
1. Cree una regla fiscal que solo se aplique a EE. UU.
1. Agregue un widget a la página de inicio que incluya más de un producto.
1. Cree dos clientes con una dirección de EE. UU. y otra que no sea de EE. UU.
1. Inicie sesión con el cliente de EE. UU. desde la tienda. Asegúrese de que la página se almacena en caché.
1. Observe el precio mostrado en el widget de página de inicio.
1. Cierre la sesión e inicie sesión con un cliente que no sea de EE. UU.

<u>Resultados esperados</u>:

El precio mostrado en el widget de página de inicio corresponde a la dirección del cliente.

<u>Resultados reales</u>:

El widget de página de inicio muestra los precios usando el impuesto para clientes que no son estadounidenses.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
