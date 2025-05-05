---
title: "ACSD-48784: Precios de segmento de cliente almacenados en caché incorrectamente entre grupos de clientes"
description: Aplique el parche ACSD-48784 para corregir el problema de Adobe Commerce en el que los precios de los segmentos del cliente se almacenan incorrectamente en caché entre grupos de clientes.
exl-id: 6be11fd0-5c93-4ac7-8664-7e2a289c9e38
feature: Admin Workspace, Cache, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-48784: precios de segmentos de clientes almacenados en caché incorrectamente entre grupos de clientes

El parche ACSD-48784 corrige el problema de que los precios de los segmentos de los clientes se almacenan incorrectamente en caché entre grupos de clientes. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28. El ID del parche es ACSD-48784. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los precios de los segmentos del cliente se almacenan incorrectamente en caché entre grupos de clientes.

<u>Requisitos previos</u>:

Configure [!DNL Varnish] o [!DNL Fastly].

<u>Pasos a seguir</u>:

1. Habilite el almacenamiento en caché de páginas completas en su tienda.
1. Inicie sesión en el sitio como usuario con precios especiales para grupos de clientes.
1. Vaya a una página de producto para un producto con precios especiales para grupos de clientes. Observe el *precio especial*.
1. En un explorador independiente, abra la misma página de producto que un usuario invitado sin iniciar sesión. Observe el precio normal.
1. Acceda a la interfaz administrativa de Adobe Commerce y borre la caché de Adobe Commerce y [!DNL Fastly] de este almacén.
1. En el explorador que inició sesión, quite la cookie `X-Magento-Vary`.
1. En el explorador que ha iniciado sesión, vuelva a cargar la misma página de producto varias veces hasta que el almacenamiento en caché se vacíe por completo.
1. En el explorador sin sesión iniciada, vuelva a cargar la página del producto para ver los precios del grupo de clientes.

<u>Resultados esperados</u>:

La página de productos muestra el precio correcto para grupos de clientes específicos.

<u>Resultados reales</u>:

* Los usuarios invitados ven el precio especial de usuario que ha iniciado sesión.
* El minicarrito muestra el precio correcto una vez que se le agrega el producto.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
