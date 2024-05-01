---
title: "ACSD-51528: Diferentes comportamientos sobre el formato snake_case"
description: Aplique el parche ACSD-51528 para corregir el problema de Adobe Commerce donde haya diferentes comportamientos en el formato snake_case.
exl-id: dd878321-8032-41f3-8dcd-acb0cc023b44
feature: Variables
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-51528: Diferentes comportamientos en el formato snake_case

El parche ACSD-51528 corrige diferentes comportamientos en el formato snake_case. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.32 está instalado. El ID del parche es ACSD-51528. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los diferentes comportamientos sobre el formato snake_case.

<u>Pasos a seguir</u>:

1. Pruebe el `\Magento\Framework\Api\DataObjectHelper::populateWithArray` función con una variedad de nombres de propiedad diferentes.
1. Las propiedades con nombres como *NewPName* debe transformarse en *new_p_name*, en cambio se están transformando en *new_pname*.
1. Además, al usar el *getNewPName* función en el objeto, *null* se devolverán porque la variable *Modelo abstracto* transformará correctamente la llamada a *new_p_name* haciendo que ambas funciones sean incompatibles entre sí.

<u>Resultados esperados</u>

El **[!UICONTROL populateWithArray]** La función debería transformar las propiedades del objeto a snake_case correctamente, haciéndolo compatible con la función **[!DNL AbstractModel's]** `Getters` y `Setters`.

<u>Resultados reales</u>

Al usar el **[!UICONTROL populateWithArray]** función, cualquier propiedad de objeto que contenga dos o más mayúsculas en una fila en su nombre hará que la transformación snake_case sea incorrecta en la matriz de datos final.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
