---
title: "ACSD-51845: No se pueden actualizar productos subsiguientes con precios de nivel y diferentes conjuntos de atributos a través de lotes asíncronos [!DNL API]"
description: Aplique el parche ACSD-51845 para solucionar el problema de Adobe Commerce, donde no puede actualizar productos posteriores con precios de nivel y diferentes conjuntos de atributos a través de lotes asíncronos [!DNL REST API].
feature: REST, Products
role: Admin
exl-id: c3fff9f2-30ad-4bcb-945e-e9e0c69630b3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51845: No se pueden actualizar productos subsiguientes con precios de nivel y diferentes conjuntos de atributos a través de lotes asíncronos [!DNL API]

El parche ACSD-51845 soluciona el problema que impide actualizar productos subsiguientes con precios de nivel y diferentes conjuntos de atributos a través de lotes asíncronos [!DNL REST API]. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.35 está instalado. El ID del parche es ACSD-51845. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La actualización falla para los productos subsiguientes con precios de nivel y diferentes conjuntos de atributos a través de lotes asíncronos [!DNL REST API].

<u>Pasos a seguir</u>:

1. Configurar [!DNL RabbitMQ].
1. Cree dos conjuntos de atributos.
1. Crear dos **Productos simples**, asignando cada producto a un conjunto de atributos diferente.
1. Añadir un **Precio de grupo de clientes** para cada producto.
1. Actualizar ambos productos de forma masiva [!DNL API] actualizar.
1. Asegúrese de que la variable `bin/magento queue:consumers:start async.operations.all` se está ejecutando.
1. Compruebe el volumen [!DNL API] estado.

<u>Resultados esperados</u>:

La ejecución del servicio se realizó correctamente.

<u>Resultados reales</u>:

El sistema devuelve el siguiente mensaje de error: *No se ha podido guardar el producto. Inténtelo de nuevo.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
