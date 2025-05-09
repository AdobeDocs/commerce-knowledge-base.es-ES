---
title: "ACSD-55305: congelación emergente durante la edición por parte del usuario de la compañía en [!UICONTROL My Account]"
description: Aplique la revisión ACSD-55305 para solucionar el problema de Adobe Commerce donde la ventana emergente [!UICONTROL Edit Company User] de la página [!UICONTROL My Account] &gt; [!UICONTROL Company Structure] se bloquea con un cargador en la pantalla.
feature: Companies, B2B
role: Admin, Developer
exl-id: be2bfe08-d05e-485d-84c3-2ff14e1a8654
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-55305: congelación emergente durante la edición por parte del usuario de la compañía en [!UICONTROL My Account]

La revisión ACSD-55305 corrige el problema en el que la ventana emergente [!UICONTROL Edit Company User] de la página [!UICONTROL My Account]> [!UICONTROL Company Structure] se bloquea con un cargador en la pantalla. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43. El ID del parche es ACSD-55305. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se produce un error al intentar usar la ventana emergente *[!UICONTROL Edit Company User]* en la página *[!UICONTROL My Account]* > *[!UICONTROL Company Structure]*, ya que se bloquea con un cargador mostrado en la pantalla.

<u>Pasos a seguir</u>:

1. Crear una compañía B2B.
1. Cree un atributo de selección múltiple para los clientes.
1. Asigne un valor al atributo recién creado para el administrador de la empresa.
1. Inicie sesión como administrador de la empresa.
1. Vaya a [!UICONTROL account dashboard] y luego a **[!UICONTROL Company Structure]**.
1. Seleccione el usuario.
1. Haga clic en **[!UICONTROL Edit Selected]**.

<u>Resultados esperados</u>:

La ventana emergente del formulario aparece con precisión y proporciona la opción de editar la información de la empresa.

<u>Resultados reales</u>:

La ventana emergente del formulario aparece sin posibilidad de edición.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
