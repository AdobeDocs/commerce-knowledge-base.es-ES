---
title: "ACSD-51899: Dirección de envío predeterminada rellenada automáticamente incorrectamente"
description: Aplique el parche ACSD-51899 para corregir el problema de Adobe Commerce en el que la dirección de envío predeterminada se rellena automáticamente con una dirección incorrecta.
feature: Checkout
role: Admin
exl-id: 67100fcd-e98f-4740-8f1f-fcc820f4c75d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-51899: la dirección de envío predeterminada se rellena automáticamente de forma incorrecta

El parche ACSD-51899 corrige el problema en el que la dirección de envío predeterminada se rellena automáticamente con una dirección incorrecta. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.35 está instalado. El ID del parche es ACSD-51899. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La dirección de envío predeterminada se rellena automáticamente con una dirección incorrecta

<u>Pasos a seguir</u>:

1. Activar **Recogida en tienda** en método de envío.
1. Crear *existencias* y *origen*.
1. Cree un producto y asígnelo al origen.
1. Añadir un producto al carro de compras.
1. Haga clic en **Continuar con el cierre** desde el minicarrito.
1. Introduzca la dirección de correo electrónico de prueba y seleccione **Elegir en tienda**.
1. Haga clic en **Seleccionar tienda** y seleccione una ubicación de tienda para elegir.
1. Haga clic en **siguiente** botón.
1. Vaya a **Página principal** haciendo clic en el logotipo de la tienda.
1. Abra el **Minicarrito**.
1. Haga clic en el hipervínculo inferior llamado **Ver y editar el carro**.
1. Clic **Continuar con el cierre**.
1. Pulsa el botón de envío de la página de envío.

<u>Resultados esperados</u>

El campo Dirección de envío permanece vacío, excepto para *País, región y código postal*.

<u>Resultados reales</u>

La dirección de envío predeterminada se rellena automáticamente con *Recogida en tienda* después de actualizar la página.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
