---
title: "ACSD-59229: Asignación incorrecta de datos del grupo de clientes debido a un valor de X-Magento-Vary obsoleto"
description: Aplique el parche ACSD-59229 para corregir el problema de Adobe Commerce en el que la información relacionada con el grupo de clientes se guarda en el segmento incorrecto debido a un valor X-Magento-Vary obsoleto en la solicitud.
feature: Customers, Personalization, Marketing Tools
role: Admin, Developer
source-git-commit: 41d502a85a0cbb4eb8d186e4c1e1256aec3f8740
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-59229: asignación incorrecta de datos del grupo de clientes debido a un valor de X-Magento-Vary obsoleto

El parche ACSD-59229 corrige el problema en el que la información relacionada con el grupo de clientes se guarda en el segmento incorrecto debido a un valor X-Magento-Vary obsoleto en la solicitud. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50. El ID del parche es ACSD-59229. Tenga en cuenta que el problema se corrige en la versión 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p8

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La información relacionada con el grupo de clientes se guarda en el segmento incorrecto debido a un valor de X-Magento-Vary obsoleto en la solicitud.

<u>Requisitos previos</u>:

Asegúrese de que Adobe Commerce B2B con datos de ejemplo esté instalado y de que [!DNL Varnish] esté configurado.

<u>Pasos a seguir</u>:

1. Configurar precios avanzados para [!DNL SKU 24-MB01]:
   1. [!UICONTROL Regular price] = *9999$*
   1. [!UICONTROL Catalog and Tier Price]:
      * *Venta al por mayor* = *$200*
      * *Minorista* = *$30*

1. Cree dos cuentas de cliente.
1. Asigne ambos clientes al grupo **Venta al por mayor**.
1. Abra dos sesiones de explorador diferentes e inicie sesión con cada cliente.
1. Vaya a la página de producto **[!UICONTROL 24-MB01]** de cada cliente y verifique que el precio mostrado sea *$200*.
1. Cambie el grupo de clientes de uno de los clientes a **Comercial**.
1. Borre la caché con el comando: `bin/magento cache:flush full_page`.
1. Actualice la página del producto para cada cliente.

<u>Resultados esperados</u>:

1. El cliente minorista puede ver el precio correcto de *$30* para el producto.
1. El cliente mayorista puede ver el precio correcto de *$200* para el producto.

<u>Resultados reales</u>:

1. El cliente minorista puede ver el precio correcto de *$30* para el producto.
1. El cliente mayorista ve un precio incorrecto de *$30* (precio minorista) para el producto.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].