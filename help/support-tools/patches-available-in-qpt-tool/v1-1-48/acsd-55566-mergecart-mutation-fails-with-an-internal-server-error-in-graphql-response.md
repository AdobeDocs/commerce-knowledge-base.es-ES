---
title: 'ACSD-55566: [!UICONTROL mergeCart] La mutación falla con un error de servidor interno en [!DNL GraphQL] response'
description: Aplique el parche ACSD-55566 para solucionar el problema de Adobe Commerce donde la mutación mergeCart falla con un error interno del servidor en [!DNL GraphQL] respuesta al combinar los carros de compras de origen y destino que tienen los mismos elementos de paquete.
feature: GraphQL, Shopping Cart
role: Admin, Developer
exl-id: 84a9b861-351e-4fcc-bb91-3e31c7ae24e6
source-git-commit: 6b8eecb3df0bb32344a5861a604a40402bb4d392
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-55566: `mergeCart` La mutación falla con un error de servidor interno en [!DNL GraphQL] respuesta

El parche ACSD-55566 corrige el problema en el que la variable `mergeCart` La mutación falla con un error interno del servidor en [!DNL GraphQL] respuesta. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 está instalado. El ID del parche es ACSD-55566. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.5.0.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6-p4

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

`mergeCart` La mutación falla con un error interno del servidor en [!DNL GraphQL] respuesta al combinar los carros de compras de origen y destino que tienen los mismos elementos de paquete.

<u>Pasos a seguir</u>:

1. Crear una fuente personalizada y un inventario personalizado.
1. Asigne las existencias creadas al sitio web principal.
1. Cree un producto simple y asígnele el origen creado (cantidad=2).
1. Cree un producto agrupado con una opción y un producto secundario (producto creado en el paso 3).
1. Crear un carro de invitados mediante [!DNL GraphQL].
1. Agregar un paquete de productos con ambas opciones seleccionadas.
1. Guarde el *cartID*.
1. Cree un cliente y genere un token de cliente.
1. Crear un carro de compras de clientes.
1. Añada el mismo producto del paquete con la misma configuración al carro de compras.
1. Intente combinar el carro de invitados con el carro de cliente.

<u>Resultados esperados</u>:

El carro del cliente contiene productos de ambos carros.

<u>Resultados reales</u>:

Se obtiene un error interno.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
