---
title: "ACSD-50336: Correos electrónicos de alerta de producto no enviados"
description: Aplique el parche ACSD-50336 para corregir el problema de Adobe Commerce donde los correos electrónicos de alerta de producto no se envían cuando un producto vuelve a estar en stock o se cambia el precio.
exl-id: 0fc51603-e74d-4ce7-9e67-42826ffbfab2
feature: Communications, Personalization, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-50336: Correos electrónicos de alerta de producto no enviados

El parche ACSD-50336 corrige el problema de que los correos electrónicos de alerta de productos no se envían cuando un producto vuelve a estar en stock o se cambia el precio. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 está instalado. El ID del parche es ACSD-50336. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p1 - 2.4.4-p2

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los correos electrónicos de alerta de producto no se envían cuando un producto vuelve a estar en stock o cuando se cambia el precio.

<u>Requisitos previos</u>:

Configure alertas de productos para cuando un producto vuelva a estar disponible.

<u>Pasos a seguir</u>:

1. Inicie sesión como cliente en la tienda.
1. Abra un producto que no esté en stock.
1. Suscríbase para recibir una notificación cuando se publique el producto *de nuevo en stock*.
1. Actualizar el producto desde [!UICONTROL Admin] para ser _de nuevo en stock_.

<u>Resultados esperados</u>:

Notificación por correo electrónico acerca del producto que se está configurando *de nuevo en stock* se envía al cliente.

<u>Resultados reales</u>:

El cliente no recibe una notificación por correo electrónico sobre el producto que se está vendiendo *de nuevo en stock*. El siguiente error aparece en el registro:

```
report. CRITICAL: Magento\ProductAlert\Model\Mailing\ErrorEmailSender::execute(): Argument #2 ($storeId) must be of type int, string given, called in vendor/magento/module-product-alert/Model/Mailing/AlertProcessor.php on line 130 [] [] 
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
