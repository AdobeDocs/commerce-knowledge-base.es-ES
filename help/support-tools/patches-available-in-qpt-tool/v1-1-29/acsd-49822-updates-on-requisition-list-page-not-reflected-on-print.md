---
title: "ACSD-49822: las actualizaciones en la página de lista de solicitudes no se reflejan en la lista de solicitudes de impresión"
description: Aplique el parche ACSD-49822 para solucionar el problema de Adobe Commerce en el que las actualizaciones de la página de lista de solicitudes no se reflejan en la lista de solicitudes de impresión.
exl-id: 584e3fcd-9153-41aa-8857-cf1fa41269c9
feature: Admin Workspace, B2B
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-49822: las actualizaciones en la lista de solicitudes no se reflejan en la lista de solicitudes de impresión

El parche ACSD-49822 soluciona el problema en el que las actualizaciones en la página de lista de solicitudes no se reflejan en la lista de solicitudes de impresión. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 está instalado. El ID del parche es ACSD-49822. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las actualizaciones en la página de lista de solicitudes no se reflejan en la lista de solicitudes de impresión.

<u>Pasos a seguir</u>:

1. Activar lista de solicitudes navegando a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[Funciones B2B]**.
1. Cree un producto.
1. Conéctese como cliente y añada dos productos a la lista de solicitudes.
1. Ir a **[!UICONTROL My Account]** > **[!UICONTROL My Requisition Lists]**.
1. Consultar una lista de solicitudes.
1. Clic **[!UICONTROL Print]** en la esquina superior derecha.
1. Cierre la ventana de impresión e imprima la página de lista de solicitudes.
1. Elimine un elemento de la lista o actualice una cantidad de un elemento e intente imprimirlo de nuevo.
1. Observará que los elementos no se actualizan en la ventana de impresión.
1. Cierre la ventana de impresión.
1. Observe que los artículos no se actualizan en la página de impresión de la lista de solicitudes.

<u>Resultados esperados</u>:

La lista que se va a imprimir se actualiza después de aplicar cualquier cambio.

<u>Resultados reales</u>:

Las actualizaciones no se reflejan en la página de impresión de la lista de solicitudes.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
