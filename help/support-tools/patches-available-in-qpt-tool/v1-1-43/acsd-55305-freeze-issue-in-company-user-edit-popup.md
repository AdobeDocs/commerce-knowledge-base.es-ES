---
title: 'ACSD-55305: congelación emergente durante la edición por parte del usuario de la empresa en [!UICONTROL My Account]'
description: Aplique el parche ACSD-55305 para solucionar el problema de Adobe Commerce donde [!UICONTROL Edit Company User] ventana emergente en [!UICONTROL My Account] &gt; [!UICONTROL Company Structure] La página se congela con un cargador en la pantalla.
feature: Companies, B2B
role: Admin, Developer
exl-id: be2bfe08-d05e-485d-84c3-2ff14e1a8654
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-55305: congelación emergente durante la edición por parte del usuario de la empresa en [!UICONTROL My Account]

El parche ACSD-55305 corrige el problema donde  [!UICONTROL Edit Company User] ventana emergente en [!UICONTROL My Account]> [!UICONTROL Company Structure] La página se congela con un cargador en la pantalla. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 está instalado. El ID del parche es ACSD-55305. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se produce un error al intentar utilizar *[!UICONTROL Edit Company User]* ventana emergente en *[!UICONTROL My Account]* > *[!UICONTROL Company Structure]* página, ya que se congela con un cargador mostrado en la pantalla.

<u>Pasos a seguir</u>:

1. Crear una compañía B2B.
1. Cree un atributo de selección múltiple para los clientes.
1. Asigne un valor al atributo recién creado para el administrador de la empresa.
1. Inicie sesión como administrador de la empresa.
1. Vaya a la [!UICONTROL account dashboard] y vaya al **[!UICONTROL Company Structure]**.
1. Seleccione el usuario.
1. Haga clic en **[!UICONTROL Edit Selected]**.

<u>Resultados esperados</u>:

La ventana emergente del formulario aparece con precisión y proporciona la opción de editar la información de la empresa.

<u>Resultados reales</u>:

La ventana emergente del formulario aparece sin posibilidad de edición.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
