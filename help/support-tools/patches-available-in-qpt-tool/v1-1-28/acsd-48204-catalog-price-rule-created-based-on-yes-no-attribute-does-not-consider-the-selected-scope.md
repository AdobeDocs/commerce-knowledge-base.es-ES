---
title: "ACSD-48204: La regla de precios de catálogo creada en función del atributo *Sí/No* no tiene en cuenta el ámbito seleccionado"
description: Aplique el parche ACSD-48204 para corregir el problema de Adobe Commerce en el que la regla de precios de catálogo creada en función del atributo *Sí/No* no tiene en cuenta el ámbito seleccionado.
exl-id: 9b0b4d62-c4c5-40d7-a279-52f59ee7ac42
feature: Admin Workspace, Attributes, Catalog Management, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# ACSD-48204: Regla de precios de catálogo creada en función de *Sí/No* el atributo no tiene en cuenta el ámbito seleccionado

El parche ACSD-48204 corrige el problema en el que la regla de precios de catálogo creada en función de *Sí/No* el atributo no tiene en cuenta el ámbito seleccionado. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 está instalado. El ID del parche es ACSD-48204. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La regla de precios de catálogo creada en función de *Sí/No* el atributo no tiene en cuenta el ámbito seleccionado.

<u>Pasos a seguir</u>:

1. Crear dos sitios web (Predeterminado y W2).
1. Crear un atributo de producto de *Sí/No* escriba.
   * Establecer [!UICONTROL Default value] = [!UICONTROL No]
   * [!UICONTROL Scope] = [!UICONTROL Website]
   * [!UICONTROL Use for Promo Rule Conditions] = [!UICONTROL Yes]
1. Cree un producto configurable basado en cualquier atributo con dos variaciones (V1 y V2).
   * Añada el *Sí/No* al conjunto de atributos de variaciones configurables
   * Para una de las variaciones (V1), establezca el valor en *[!UICONTROL Yes]* en el sitio web no predeterminado (W2)
1. Crear una regla de catálogo:
   * Se aplica a ambos sitios web
   * Condición: *Sí/No* el valor del atributo es *[!UICONTROL Yes]*
   * Descuento = 50 %
1. Abra el producto configurable en el sitio web no predeterminado (W2).
1. Compruebe que la variación V1 tenga el descuento del 50 % aplicado.
1. Abra la variación V1 en el Administrador de Adobe Commerce.
   * Cambiar al sitio web predeterminado
   * No realice cambios y guarde el producto
1. Actualice la página de tienda de productos configurable.

<u>Resultados esperados</u>:

La variación V1 sigue teniendo el descuento del 50 % aplicado, ya que no se han realizado cambios.

<u>Resultados reales</u>:

El descuento desaparece.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
