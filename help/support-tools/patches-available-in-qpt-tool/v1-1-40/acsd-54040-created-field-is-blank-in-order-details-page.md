---
title: '''ACSD-54040: El [!UICONTROL Created] El campo está en blanco para obtener detalles del pedido cuando los módulos B2B están activados.'
description: Aplique el parche ACSD-54040 para solucionar el problema de Adobe Commerce donde la variable [!UICONTROL Created] El campo está en blanco en la página de detalles del pedido cuando los módulos B2B están activados.
feature: B2B
role: Admin, Developer
exl-id: 5c420b94-43e1-40ac-9482-8a2d42f173d9
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-54040: *[!UICONTROL Created]* El campo está en blanco para obtener detalles del pedido cuando los módulos B2B están activados.

El parche ACSD-54040 corrige el problema en el que la variable *[!UICONTROL Created]* El campo permanece en blanco en la página de detalles del pedido cuando los módulos B2B están activados. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 está instalado. El ID del parche es ACSD-54040. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p5, 2.4.4-p6, 2.4.5-p4, 2.4.5-p5

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando los módulos B2B están activados, la variable *[!UICONTROL Created]* permanece en blanco en la página de detalles del pedido.

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce con el módulo B2B.
1. Cree un nuevo cliente y realice un pedido.
1. Vaya a los detalles del pedido en el front-end y compruebe la *[!UICONTROL Created]* field.

<u>Resultados esperados</u>:

El *[!UICONTROL Created]* El campo muestra la fecha en la que se creó el pedido.

<u>Resultados reales</u>:

El *[!UICONTROL Created]* el campo está en blanco

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
