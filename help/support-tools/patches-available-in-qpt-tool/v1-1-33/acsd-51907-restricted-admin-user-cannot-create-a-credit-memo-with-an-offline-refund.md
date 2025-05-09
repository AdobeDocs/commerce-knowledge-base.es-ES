---
title: "ACSD-51907: El usuario administrador restringido no puede crear un abono para el reembolso sin conexión"
description: Aplique el parche ACSD-51907 para solucionar el problema de Adobe Commerce en el que el usuario administrador restringido no puede crear un abono con un reembolso sin conexión.
exl-id: 564e8524-f2dc-453c-be78-a920fbd47d71
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-51907: el usuario administrador restringido no puede crear un abono para el reembolso sin conexión

El parche ACSD-51907 corrige el problema de rendimiento en el que el usuario administrador restringido no puede crear un abono con un reembolso sin conexión. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.33. El ID del parche es ACSD-51907. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 &lt; 2.4.3-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario administrador restringido no puede crear un abono con un reembolso sin conexión.

<u>Pasos a seguir</u>:

1. Crear un **cliente** en el sitio web predeterminado.
1. Crear **nuevo sitio web** con *tienda* y *vista de tienda* relacionados.
1. Configure el sitio web predeterminado en el nuevo sitio web y borre las cachés.
1. Cambiar la configuración del cliente: **Administrador** > **Tienda** > **Configuración** > **Clientes** > **Configuración del cliente** > **Compartir cuentas de cliente = Global**.
1. Cree un nuevo rol de usuario administrador con el ámbito de rol establecido en el nuevo sitio web creado *(solo acceso a datos de ventas)* en **Administración** > **Sistema** > **Permisos**.
1. Cree una nueva cuenta de administrador con esta función.
1. Cree un nuevo pedido con el método de pago en línea *(por ejemplo, Auth.net o PayPal)*.
1. Inicie sesión como usuario administrador restringido.
1. Vaya a **Ventas** > **Pedidos** > y luego a **página de vista de pedidos**.
1. Crear una factura.
1. Acceda a la pestaña Facturas.
1. Haz clic en **Factura**.
1. Haga clic en **[!UICONTROL Credit Memo]**.
1. Marque la casilla de verificación **[!UICONTROL Refund to Store Credit]** y establezca el campo de texto que está cerca de él en el valor *1*.
1. Haga clic en el botón **[!UICONTROL Refund Offline]**.

<u>Resultados esperados</u>:

Se crea el abono y *$1* se devuelve al abono de la tienda.

<u>Resultados reales</u>:

Se muestra el mensaje de error *Se necesitan más permisos para ver este elemento*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
