---
title: "ACSD-52277: El usuario administrador redirigió incorrectamente al seleccionar la vista de la tienda al crear un nuevo pedido"
description: Aplique el parche ACSD-52277 para corregir el problema de Adobe Commerce en el que un usuario administrador no se redirige correctamente después de seleccionar la vista de tienda al crear un nuevo pedido en Administración.
exl-id: 6f0b86ae-f6f1-44cf-aef5-64def5f14824
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-52277: el usuario administrador redireccionaba incorrectamente al seleccionar la vista de la tienda al crear un nuevo pedido

El parche de ACSD-52277 corrige el problema en el que un usuario administrador no se redirige correctamente después de seleccionar la vista de la tienda al crear un nuevo pedido en Administración. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34 está instalado. El ID del parche es ACSD-52277. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4, 2.4.6

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Un usuario administrador no se redirige correctamente después de seleccionar la vista de la tienda al crear un nuevo pedido.

<u>Pasos a seguir</u>

1. Instale una instancia limpia.
1. Cree un producto.
1. Cree un sitio web, una tienda y dos vistas de la tienda adicionales.
1. Cree un pedido desde el administrador seleccionando *vista de tienda 1*.

<u>Resultados esperados</u>:

Se redirige al usuario a la página de pedidos.

<u>Resultados reales</u>:

No se redirige al usuario a la página de pedidos después de seleccionar la vista de la tienda.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
