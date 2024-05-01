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

El parche ACSD-51907 corrige el problema de rendimiento en el que el usuario administrador restringido no puede crear un abono con un reembolso sin conexión. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.33 está instalado. El ID del parche es ACSD-51907. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 &lt; 2.4.3-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario administrador restringido no puede crear un abono con un reembolso sin conexión.

<u>Pasos a seguir</u>:

1. Crear un **cliente** en el sitio web predeterminado.
1. Crear **nuevo sitio web** con elementos relacionados *almacenar* y *vista de tienda*.
1. Configure el sitio web predeterminado en el nuevo sitio web y borre las cachés.
1. Cambiar la configuración del cliente: **Administrador** > **Almacenar** > **Configuración** > **Clientes** > **Configuración del cliente** > **Compartir cuentas de cliente = Global**.
1. Crear un nuevo rol de usuario administrador con el ámbito de rol establecido en el nuevo sitio web creado *(solo acceso a datos de ventas)* in **Administrador** > **Sistema** > **Permisos**.
1. Cree una nueva cuenta de administrador con esta función.
1. Crear nuevo pedido con el método de pago en línea *(por ejemplo, Auth.net o PayPal)*.
1. Inicie sesión como usuario administrador restringido.
1. Ir a **Ventas** > **Pedidos** > then **página de vista de pedidos**.
1. Crear una factura.
1. Acceda a la pestaña Facturas.
1. Haga clic en **Factura**.
1. Haga clic en **[!UICONTROL Credit Memo]**.
1. Compruebe la **[!UICONTROL Refund to Store Credit]** casilla de verificación, establezca el campo de texto cerca de él en el *1* valor.
1. Haga clic en **[!UICONTROL Refund Offline]** botón.

<u>Resultados esperados</u>:

Se crea la nota de abono y *$1* se reembolsa al crédito de la tienda.

<u>Resultados reales</u>:

El mensaje de error, *Se necesitan más permisos para ver este elemento* se muestra.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
