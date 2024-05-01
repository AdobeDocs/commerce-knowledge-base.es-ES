---
title: "ACSD-51630: Numerosos mensajes del sistema ralentizan la descarga de las páginas de administración"
description: Aplique el parche ACSD-51630 para solucionar el problema de rendimiento de Adobe Commerce, donde una gran cantidad de mensajes del sistema ralentiza la descarga de las páginas de administración.
feature: Admin Workspace, System
role: Admin
exl-id: 28f85199-625e-4299-bbca-8d2fc75df602
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# ACSD-51630: Numerosos mensajes del sistema ralentizan la descarga de las páginas de administración

El parche ACSD-51630 corrige el problema de rendimiento en el que una gran cantidad de mensajes del sistema ralentiza la descarga de las páginas de administración. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.34 está instalado. El ID del parche es ACSD-51630. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 &lt; 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Numerosos mensajes del sistema ralentizan la descarga de las páginas de administración

<u>Pasos a seguir</u>:

1. Realizar una gran cantidad de solicitudes (~50 000) al DELETE `/rest/async/v1/products/ {sku}`.
1. Acceder a cualquiera **Página de administración**.

<u>Resultados esperados</u>:

La página se carga en un momento adecuado. Solo se deben cargar los mensajes que se muestran.

<u>Resultados reales</u>:

La página tarda demasiado en cargarse. Todos los mensajes existentes se cargan desde la base de datos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
