---
title: "ACSD-55241: **Utilizado** y **Tiempos utilizado** muestran valores incorrectos para los cupones generados"
description: Aplique el parche ACSD-55241 para solucionar el problema de Adobe Commerce donde los atributos **Utilizado** y **Tiempos utilizado** muestran valores incorrectos para los cupones generados
feature: Price Rules
role: Admin, Developer
exl-id: cfe0f8af-423a-4e12-a332-053392cbabed
source-git-commit: 5d0b4743fe49d22c099102490f93dc4065ab4413
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-55241: **Utilizado** y **Horas utilizadas** Los atributos de muestran valores incorrectos para los cupones generados

El parche ACSD-55241 corrige el problema en el que la variable **Utilizado** y **Horas utilizadas** Los atributos de muestran valores incorrectos para los cupones generados. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.47 está instalado. El ID del parche es ACSD-55241. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

**Utilizado** y **Horas utilizadas** Los atributos de muestran valores incorrectos para los cupones generados.

<u>Pasos a seguir</u>:

1. Crear **[!UICONTROL Cart Price Rules]** de **[!UICONTROL Admin]** > **[!UICONTROL Marketing]** > **[!UICONTROL Promotion]** y añada cualquier condición que coincida al realizar un pedido (por ejemplo: subtotal mayor que *5$*)

* Aplicar cualquier descuento.
* Seleccionar **[!UICONTROL Auto Coupon]**.
* Se generan algunos Códigos de cupón a partir de **Administrar códigos de cupones**.
* Reindexe y limpie la caché.

1. Crear un **[!UICONTROL customer account]** e inicie sesión en el front-end.
1. Añadir un producto con más de *2* cantidades en el carro de compras y aplique un cupón.
1. Haga clic en **[!UICONTROL Check Out with Multiple Addresses]**.
1. Seleccione una dirección distinta para cada cantidad, realice el pedido y complete el proceso de cierre de compra.
1. Observe el total del pedido del administrador y vea el descuento aplicado.
1. Realice otro pedido con otro cupón.
1. Ejecute el `php81 bin/Magento queue:consumers: start sales.rule.update.coupon.usage &` para actualizar el uso del código de cupón.

<u>Resultados esperados</u>:

El recuento correcto debe mostrarse en la **Tiempo utilizado** y **Utilizado** columnas con **Sí** valor de **[!UICONTROL manage coupon]** en el **[!UICONTROL cart price rule]** en el administrador.

<u>Resultados reales</u>:

El recuento de código de cupón utilizado no se actualiza en la **Tiempo utilizado** de la cuadrícula cupones y la columna **Utilizado** La columna muestra el *No* valor si realiza un pedido con varias direcciones de envío.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
