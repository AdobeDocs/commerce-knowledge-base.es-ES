---
title: '''ACSD-50895: [!DNL Google Analytics] 3 Las etiquetas GTM no se activan si [!DNL Google Analytics] 4 "La GTM no está configurada"'
description: Aplique el parche ACSD-50895 para solucionar el problema de Adobe Commerce donde [!DNL Google Analytics] 3 Las etiquetas GTM no se activan si [!DNL Google Analytics] 4 La GTM no está configurada.
role: Admin
exl-id: da48f6f1-a68b-4a9c-a79a-d7bd01b65dc2
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-50895: [!DNL Google Analytics] 3 Las etiquetas GTM no se activan si [!DNL Google Analytics] 4 La GTM no está configurada

El parche ACSD-50895 corrige el problema donde [!DNL Google Analytics] 3 Las etiquetas GTM no se activan si [!DNL Google Analytics] 4 La GTM no está configurada. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 está instalado. El ID del parche es ACSD-50895. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

[!DNL Google Analytics] 3 Las etiquetas GTM no se activan si [!DNL Google Analytics] 4 La GTM no está configurada.

<u>Pasos a seguir</u>:

1. Inicie sesión como usuario administrador.
1. Activar **[!DNL Google Analytics 3]** y **[!DNL Google Tag Manager]** in **Administrador** > **Almacenar** > **Configuración** > **Ventas** > **API de Google** > **Google Analytics**.
1. No habilite la variable **[!DNL Google Analytics 4]** y **[!DNL Google Tag Manager]**.
1. Abra la página del producto en la Tienda.

<u>Resultados esperados</u>:

Las etiquetas GTM se activan cuando solo **[!DNL Google Analytics]** 3 La GTM está activada.

<u>Resultados reales</u>:

Las etiquetas GTM no se activan cuando **[!DNL Google Analytics]** 4 La GTM está desactivada.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
