---
title: "ACSD-52219: resolviendo el problema de filtro de las cuadrículas de administración en el cambio de vista de marcadores"
description: Aplique el parche ACSD-52219 para corregir el problema de Adobe Commerce en el que los filtros guardados de las cuadrículas de administración no funcionan como se espera cuando se cambia con frecuencia entre vistas de marcadores.
feature: Admin Workspace
role: Admin
exl-id: e8333ee7-28a8-4457-aeff-6828f8ca9412
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-52219: resolviendo el problema de filtro de las cuadrículas de administración en el cambio de vista de marcadores

El parche ACSD-52219 soluciona el problema de que los filtros guardados de las cuadrículas de administración no funcionan como se esperaba cuando se cambia con frecuencia entre vistas de marcadores. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39 está instalado. El ID del parche es ACSD-52219. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al cambiar con frecuencia entre las vistas de marcadores, los filtros guardados en las cuadrículas de administración no funcionan según lo previsto.

<u>Pasos a seguir</u>:

1. Acceda a la [!DNL Sales Order] en la pestaña Administración.
1. Cree de dos a tres filtros.
1. Compruebe la configuración del filtro cambiando de vista para asegurarse de que se guarda con precisión.
1. Vaya a Filter1 o Filter2.
1. Actualice la página para actualizar los datos mostrados.
1. Cambie a una vista diferente y observe que los filtros permanecen inalterados.
1. Observe que la vista predeterminada ahora muestra los resultados filtrados, aunque no se haya establecido ningún filtro específico para ella.

<u>Resultados esperados</u>:

Los filtros no se intercambian y conservan su estado original.

<u>Resultados reales</u>:

Al modificar una vista, los filtros se mezclan y la vista correcta no se guarda.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
