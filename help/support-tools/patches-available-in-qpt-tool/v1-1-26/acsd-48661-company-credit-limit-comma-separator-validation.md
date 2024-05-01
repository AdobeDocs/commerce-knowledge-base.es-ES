---
title: "ACSD-48661: problema de validación del separador de comas del límite de crédito de la empresa"
description: Aplique el parche ACSD-48661 para corregir el problema de Adobe Commerce en el que, cuando el límite de crédito de la empresa es mayor que 999, el separador de comas impide que se guarde la empresa debido a un error de validación.
exl-id: 85c5a93f-76c5-439b-adcc-511f8473f302
feature: Admin Workspace, B2B, Companies, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-48661: problema de validación del separador de comas del límite de crédito de la empresa

El parche ACSD-48661 corrige el problema en el que cuando el límite de crédito de la empresa es mayor que 999, el separador de comas impide el guardado de la empresa debido a un error de validación. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 está instalado. El ID del parche es ACSD-48661. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando el límite de crédito de la empresa es mayor que 999, el separador de comas impide que la empresa guarde debido a un error de validación.

<u>Pasos a seguir</u>:

1. Habilite la función de empresa en **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Cree una empresa y añada un límite de crédito superior a 999 en la variable **[!UICONTROL Company Credit]** pestaña.
1. Guarde la compañía.
1. Edite la empresa e intente guardarla de nuevo.

<u>Resultados esperados</u>:

Puede salvar a la empresa sin fijar el límite de crédito. La coma no es compatible con los campos de entrada para las cantidades y los precios.

<u>Resultados reales</u>:

No puede guardar la empresa debido a un error de validación en *[!UICONTROL Credit Limit]* field. Adobe Commerce agrega automáticamente separadores de coma para los límites de crédito aunque la variable [!UICONTROL Credit Limit] El campo no acepta comas.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
