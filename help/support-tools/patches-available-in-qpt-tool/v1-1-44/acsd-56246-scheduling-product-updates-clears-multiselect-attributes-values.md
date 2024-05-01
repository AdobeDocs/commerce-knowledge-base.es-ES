---
title: "ACSD-56246: al programar actualizaciones de productos, se borran los valores de atributos multiselect"
description: Aplique el parche ACSD-56246 para corregir el problema de Adobe Commerce donde la programación de actualizaciones de productos borra los valores de atributos de selección múltiple.
feature: Products, Attributes, Staging
role: Admin, Developer
exl-id: ddca8ac0-6aa8-4bf1-b8c2-4819758cb198
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-56246: al programar actualizaciones de productos se borran los valores de atributos de selección múltiple

El parche ACSD-56246 corrige el problema en el que la programación de actualizaciones de productos borra los valores de atributos de selección múltiple. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 está instalado. El ID del parche es ACSD-56246. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las actualizaciones de productos programadas borran los valores de atributos multiselect.

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce.
1. Ir a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** y cree el atributo siguiente:

   * Etiqueta predeterminada: Programa
   * Tipo de entrada de catálogo para el propietario de la tienda: Selección múltiple
   * Administrar opciones (valores de su atributo): Choice, Sunscape, Safetyshield
   * Código de atributo: customer_program
   * Ámbito: Global
   * Agregar a opciones de columna: No
   * Uso en las opciones de filtro: no
   * Propiedades de tienda
   * Posición: *333*
   * Permitir etiquetas de HTML en tienda: No

1. Ejecutar
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Ejecutar
   `bin/magento setup:upgrade`.
1. Vaya a la **[!UICONTROL Admin]** > Seleccionar cualquier producto simple > Seleccionar todos los artículos en el atributo del programa > Haga clic en **[!UICONTROL Save the product]**.
1. Programe una actualización para este producto en el siguiente minuto y ejecute el siguiente comando para que el ensayo de contenido funcione:
   `for i in {1..100}; do bin/magento cron:run; done`.

<u>Resultados esperados</u>:

El producto está **[!UICONTROL program]** el atributo no debe cambiar.

<u>Resultados reales</u>:

El producto está **[!UICONTROL program]** se borra el atributo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
