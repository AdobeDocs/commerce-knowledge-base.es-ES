---
title: "ACSD-53643: El pedido tiene un total incorrecto al realizar un pedido de compra"
description: Aplique el parche ACSD-53643 para solucionar el problema de Adobe Commerce en el que el pedido tiene un total incorrecto al realizar un pedido de compra con productos desactivados o sin existencias.
feature: B2B
role: Admin, Developer
exl-id: 9843e07a-8a17-401e-98bc-559df5148d34
source-git-commit: 2356ac10b05ae9f38e5c0ca90d9156b0fc405718
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# ACSD-53643: el pedido tiene un total incorrecto al realizar un pedido de compra

El parche ACSD-53643 corrige el problema en el que el pedido tiene un total incorrecto al realizar un pedido de compra con productos desactivados o sin existencias. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 está instalado. El ID del parche es ACSD-53643. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El total del pedido es incorrecto al realizar un pedido de compra con productos desactivados o sin existencias.

<u>Pasos a seguir</u>:

1. Instalar *[!UICONTROL B2B]* y *[!UICONTROL Inventory]*.
1. Ir a **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B]** y establecer **[!UICONTROL Company]** = *Sí* y **[!UICONTROL Purchase Order]** = *Sí*.
1. Borre la caché de configuración.
1. Crear una nueva compañía, activarla y habilitar *[!UICONTROL Purchase order]* para la empresa.
1. Cree un nuevo usuario para la compañía.
1. Crear un *Regla de aprobación* para aprobar todas las solicitudes de más de *1 USD* por el administrador de la empresa.
1. Cree una fuente adicional.
1. Inicie sesión como el nuevo usuario de la empresa.
1. Añada dos productos al carro de compras y realice un pedido de compra.
1. Deshabilite el segundo producto.
1. Inicie sesión como administrador de la empresa.
1. Abra el pedido de compra y compruebe que el pedido contiene ambos productos y que el total es para ambos.
1. Apruebe el pedido de compra.
1. Realice el pedido.
1. Abra los detalles del pedido.

<u>Resultados esperados</u>:

* No se puede realizar el pedido aunque haya un producto en el pedido *inhabilitado* o *sin existencias*.
* *[!UICONTROL Place Order]* El botón está oculto.

<u>Resultados reales</u>:

El pedido realizado contiene únicamente el primer producto activo, pero el total del pedido se calcula para ambos productos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
