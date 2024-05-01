---
title: "ACSD-51645: Guardar una nueva regla de precio del carro de compras si la extensión Magento_OfflineShipping está deshabilitada"
description: Aplique el parche ACSD-51645 para corregir el problema de Adobe Commerce en el que se produce un error al guardar una nueva regla de precio del carro de compras si la extensión Magento_OfflineShipping está desactivada.
exl-id: 301086bb-7aab-4e74-93e6-9080eebcb026
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-51645: Guardar una nueva regla de precio del carro de compras si la extensión Magento_OfflineShipping está desactivada

El parche ACSD-51645 corrige el problema en el que se produce un error al guardar una nueva regla de precio del carro de compras si la extensión Magento_OfflineShipping está desactivada. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 está instalado. El ID del parche es ACSD-51645. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se produce un error al guardar una nueva regla de precio del carro de compras si la extensión `Magento_OfflineShipping` está deshabilitada.

<u>Pasos a seguir</u>:

1. Desactivar el `Magento_OfflineShipping` módulo.
1. Iniciar sesión en **Administrador**.
1. Ir a **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]**.
1. Crear un nuevo **[!UICONTROL Cart Price Rule]**.
1. Rellene los campos obligatorios.
1. Guarde el **[!UICONTROL Cart Price Rule]**.

<u>Resultados esperados</u>:

La regla de precio del carro de compras se ha guardado correctamente.

<u>Resultados reales</u>:

Se produce el siguiente error:
`report.ERROR: Warning: Undefined array key "simple_free_shipping" in app/code/Magento/SalesRule/Controller/Adminhtml/Promo/Quote/Save.php on line 67 [] []`

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) en el [!DNL Quality Patches Tool] guía.
