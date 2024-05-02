---
title: "ACSD-58008: Si edita la fecha de finalización como *empty*, la actualización de la programación desaparece"
description: Aplique el parche ACSD-58008 para corregir el problema de Adobe Commerce en el que editar la fecha de finalización como *empty* hace que desaparezca la actualización de la programación.
feature: Staging, Page Content
role: Admin, Developer
source-git-commit: 174ed3b35edeb26b09b04bc7d88111a5719e08f8
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-58008: Edición de la fecha de finalización como *vaciar* hace que desaparezca la actualización de la programación

El parche ACSD-58008 corrige el problema en el que al editar la fecha de finalización como *vaciar* hace que desaparezca la actualización de la programación. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 está instalado. El ID del parche es ACSD-58008. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p5

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Edición de la fecha de finalización como *vaciar* hace que desaparezca la actualización de la programación

<u>Pasos a seguir</u>:

1. Iniciar sesión como [!UICONTROL Admin].
1. Ir a **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** y cree una página.
1. Seleccione la página creada y haga clic en **[!UICONTROL Schedule New Update]**. *(Navegue por ella en la esquina superior derecha de la página)*.
1. Cree cuatro actualizaciones. *(Por ejemplo, como incremento de* 2 *minutes)*.
1. Actualice el *actualización 2* y cambie la hora a una hora que esté adelantada a la última *actualización 4*.
1. Guarde las actualizaciones realizadas.

<u>Resultados esperados</u>:

La actualización de programación muestra el *actualización 3*.

<u>Resultados reales</u>:

La actualización de programación no muestra el *actualización 3*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.