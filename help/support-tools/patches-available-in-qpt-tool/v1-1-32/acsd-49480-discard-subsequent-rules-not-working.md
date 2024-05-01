---
title: "ACSD-49480: descartar las reglas posteriores que no funcionen"
description: Aplique el parche ACSD-49480 para solucionar el problema de Adobe Commerce donde la variable [!UICONTROL Cart Price Rule - Discard Subsequent Rules] no funciona como estaba previsto.
exl-id: 8d306a9e-ed1a-4295-8130-81700cbf31a6
feature: Price Rules
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-49480: [!UICONTROL Cart Price Rule - Discard Subsequent Rules] no funciona como estaba previsto

El parche ACSD-49480 corrige el problema en el que la variable [!UICONTROL Cart Price Rule - Discard Subsequent Rules] no funciona como estaba previsto. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.32 está instalado. El ID del parche es ACSD-49480. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.5

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

[!UICONTROL Cart Price Rule - Discard Subsequent Rules] no funciona como estaba previsto.

<u>Pasos a seguir</u>:

1. Crear un **[!UICONTROL Cart Price Rule]** con un código de cupón (asígnele el nombre *PRUEBA*) que otorga un descuento de 10 $ a la *ID de producto 1* en el **[!UICONTROL Actions]** pestaña con [!UICONTROL Discard Subsequent Rules] establezca en *[!UICONTROL Yes]* y [!UICONTROL Priority] establezca en *1*.
1. Crear otro **[!UICONTROL Cart Price Rule]** sin un código de cupón que ofrezca un descuento de 5 $ a *ID de producto 2* en el **[!UICONTROL Actions]** pestaña con [!UICONTROL Priority] establezca en *2*. Aquí, asumimos, esta es una venta global para *ID de producto 2*.
1. Vaya al sitio de front-end y añada *ID de producto 1* y *ID de producto 2* en el carro de compras.
1. Aplique la variable *PRUEBA* código de cupón.

<u>Resultados esperados</u>

* *Descuento 1* se aplica a *ID de producto 1*.
* *Descuento 2* se aplica a *ID de producto 2*.

<u>Resultados reales</u>

* Solo *Descuento 1* se aplica a *ID de producto 1*.
* *Descuento 2* no se aplica a *ID de producto 2*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
