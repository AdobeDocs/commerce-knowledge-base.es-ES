---
title: "ACSD-56886: El producto configurable se queda sin existencias cuando los productos secundarios están desactivados"
description: Aplique el parche ACSD-56886 para corregir el problema de Adobe Commerce en el que el producto configurable se queda sin existencias secundario cuando los productos están desactivados.
feature: Products
role: Admin, Developer
exl-id: 809b9829-283f-4e3c-bf27-1944057f944f
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-56886: el producto configurable se queda sin existencias cuando los productos secundarios están desactivados

El parche ACSD-56886 corrige el problema en el que el producto configurable se queda sin existencias cuando se desactivan los productos secundarios. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 está instalado. El ID del parche es ACSD-56886. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p5

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El producto configurable se queda sin existencias cuando los productos secundarios están desactivados.

<u>Pasos a seguir</u>:

1. Inicie sesión como administrador.
1. Establezca todos los indexadores en la **[!UICONTROL Update By Schedule]** modo.
1. Cree el siguiente producto configurable:

   * Nombre = *PRUEBA CONFIGURABLE 1*
   * Atributo = *color*
   * Valores = *rojo* y *black*
   * Precio de la **rojo**  producto secundario = *100 $*;
   * Precio del producto secundario &quot;negro&quot; = *200 $*.

1. Cree la siguiente actualización programada para el producto configurable:

   * Fecha de inicio = *3* minutos a partir de ahora.
   * Fecha de finalización = *5* minutos después de la fecha de inicio.
   * Nombre del producto = *PRUEBA CONFIGURABLE 1 editada*.
   * Desactivar el **rojo** producto secundario en **Configurable** sección.

1. Espere a la fecha de inicio.
1. Abra los detalles configurables del producto en la Tienda.

<u>Resultados esperados</u>:

El producto configurable se muestra como **En stock** con el **Tan bajo como 200** etiqueta.

<u>Resultados reales</u>:

El producto configurable se muestra como **Sin existencias**.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
