---
title: "ACSD-57565: El panel de pedidos muestra información de pedidos incorrecta"
description: Aplique el parche ACSD-57565 para corregir el problema de Adobe Commerce en el que el panel de pedidos muestra información de pedidos incorrecta hasta que se actualiza el periodo de tiempo.
feature: Roles/Permissions
role: Admin, Developer
exl-id: 5b292fef-23f6-479f-bf76-adad53d30cf4
source-git-commit: fdf6e6e85f903a26a7b44674937ccf88ee769d06
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-57565: El panel de pedidos muestra información de pedidos incorrecta

El parche ACSD-57565 corrige el problema en el que el panel de pedidos muestra información de pedidos incorrecta hasta que se actualiza el periodo de tiempo. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.48 está instalado. El ID del parche es ACSD-57565. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche

## Problema

El panel de pedidos muestra información de pedidos incorrecta.

<u>Pasos a seguir</u>:

1. Activar **[!UICONTROL dashboard charts]**.
1. Crear un pedido y facturarlo.
1. Espere al menos 24 horas después de la hora de creación del pedido.
1. Compruebe la **[!UICONTROL dashboard chart]** datos.
1. Tome nota del recuento completo del pedido.
1. Cambie la hora a *mes actual* y vuelva a cambiarlo a *hoy*.

<u>Resultados esperados</u>:

El gráfico del panel debe mostrar las estadísticas correctas todo el tiempo.

<u>Resultados reales</u>:

El gráfico del panel muestra estadísticas incorrectas en la primera carga. Las estadísticas precisas del gráfico se actualizan después del período de tiempo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
