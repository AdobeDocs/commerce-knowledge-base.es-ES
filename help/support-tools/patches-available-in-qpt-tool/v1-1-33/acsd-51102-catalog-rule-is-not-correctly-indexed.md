---
title: "ACSD-51102: La regla de catálogo aplicada a un gran número de productos no indexados correctamente"
description: Aplique el parche ACSD-51102 para corregir el problema de Adobe Commerce en el que una regla de catálogo aplicada a un gran número de productos no se indexa correctamente cuando una actualización programada habilita la regla.
feature: Catalog Management, Products
role: Admin
exl-id: 5c1c5f9c-9cce-4b11-8058-0e12a4bf93fd
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# ACSD-51102: La regla de catálogo aplicada a un gran número de productos no está indexada correctamente

El parche ACSD-51102 corrige el problema de que una regla de catálogo aplicada a un gran número de productos no se indexa correctamente cuando la regla está habilitada por una actualización programada. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 está instalado. El ID del parche es ACSD-51102. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Una regla de catálogo aplicada a un gran número de productos no se indexa correctamente cuando una actualización programada activa la regla.

Requisitos previos:

* El trabajo de cron se configura y se ejecuta cada minuto.

<u>Pasos a seguir</u>:

1. Cree un catálogo grande con miles de productos para conseguir el tiempo de ejecución del *regla de catálogo* indexadores de más de 120 segundos cuando se activan las reglas de catálogo.
2. Cree dos reglas de catálogo con *Activo* estado establecido en *No*.  Por ejemplo, *Prueba 1* y *Prueba 2*. Cada regla debe afectar a todos los productos del catálogo y hacer que el indexador se ejecute durante más de 120 segundos.
3. Asegúrese de que el estado del indizador es *Listo*.
4. Cree actualizaciones programadas para habilitar estas dos reglas. *Prueba 2* la programación debe iniciarse poco después de *Prueba 1*. Por ejemplo, con una diferencia de 1 minuto.
5. Consulta los precios de los productos en la Tienda.

<u>Resultados esperados</u>

Se aplican descuentos de ambas reglas.

<u>Resultados reales</u>

Solo se aplica el primer descuento de regla.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) en el [!DNL Quality Patches Tool] guía.
