---
title: 'ACSD-47232: el cupón no se aplica cuando [!UICONTROL Same as Billing Address] está marcado'
description: Aplique el parche ACSD-47232 para corregir el problema de Adobe Commerce en el que el cupón no se aplica cuando [!UICONTROL Same as Billing Address] está marcada.
exl-id: 29b95a0b-8792-4830-a1e5-ce977f8453ec
feature: Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-47232: el cupón no se aplica cuando [!UICONTROL Same as Billing Address] está marcado

El parche ACSD-47232 corrige el problema en el que el cupón no se aplica cuando **[!UICONTROL Same as Billing Address]** está marcada. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 está instalado. El ID del parche es ACSD-47232. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El cupón no se aplica cuando **[!UICONTROL Same as Billing Address]** está marcada.

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce.
1. Cree un producto simple con weight = *8*.
1. Crear un cliente nuevo con la dirección de facturación y envío predeterminada.
1. Cree una regla de precio de carro de compras con un cupón.
   * Entrada **[!UICONTROL Conditions]** secciones, añadir *Peso total igual o superior a 5*
1. Intente crear un nuevo orden en la [!UICONTROL Commerce] Administrador.
   * Utilice el cliente creado justo ahora
   * Agregar un producto
   * Intente aplicar el cupón

<u>Resultados esperados</u>:

Se aplica el cupón.

<u>Resultados reales</u>:

Se obtiene un error similar al siguiente: *El código de cupón 123 no es válido. Compruebe el código e inténtelo de nuevo.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
