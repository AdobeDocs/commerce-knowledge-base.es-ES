---
title: "ACSD-52041: El procesamiento de Page Builder no libera bloqueos"
description: Aplique el parche ACSD-52041 para corregir el problema de Adobe Commerce en el que Page Builder se procesa durante cinco segundos sin liberar bloqueos.
feature: Page Builder
role: Admin, Developer
exl-id: f2a1fd36-2098-46a7-aa42-3a5a0014adc9
source-git-commit: b5c253a5c0651c6027c0795edb2f230bd65f734a
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# ACSD-52041: El procesamiento de Page Builder no libera bloqueos

El parche ACSD-52041 corrige el problema en el que Page Builder se procesa durante cinco segundos sin liberar bloqueos. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.48. El ID del parche es ACSD-52041-v2. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4: 2.4.4-p5, 2.4.5: 2.4.5-p4 y 2.4.6: 2.4.6-p2.



>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.


## Problema

**[!DNL Page Builder]** se procesa durante *5* segundos sin liberar los bloqueos.

<u>Pasos a seguir</u>:

1. Edite una página de CMS, una página de producto o cualquier elemento que tenga **[!DNL Page Builder]**.
1. Guarde los cambios.
1. Observe cómo la página ahorra tiempo.

<u>Resultados esperados</u>

El contenido se guarda. No se encontraron errores en el registro del explorador.

<u>Resultados reales</u>

El guardado tarda más de lo normal en completarse.
Error en la consola: ``Page Builder was rendering for 5 seconds without releasing locks``

## Aplicar el parche

Para aplicar parches individuales para las versiones **2.4.4 - 2.4.4-p5, 2.4.5 - 2.4.5-p4 y 2.4.6 - 2.4.6-p2**, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es>) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es>) en la guía [!DNL Quality Patches Tool].
