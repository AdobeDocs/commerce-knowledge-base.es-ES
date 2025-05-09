---
title: "MDVA-37725: Los correos electrónicos enviados a través de sitios no predeterminados contienen las URL del logotipo del sitio predeterminado"
description: El parche MDVA-37725 corrige el problema de que los correos electrónicos de pedido asincrónico se envían a través de sitios web no predeterminados que contienen direcciones URL de logotipo del sitio web predeterminado.
exl-id: c0d1b9a3-01bb-445b-b7da-f9be6952eaeb
feature: Communications, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-37725: Los correos electrónicos enviados a través de sitios no predeterminados contienen las direcciones URL del logotipo del sitio predeterminado

>[!WARNING]
>
> El parche de MDVA-37725 está obsoleto.

El parche MDVA-37725 corrige el problema de que los correos electrónicos de pedido asincrónico se envían a través de sitios web no predeterminados que contienen direcciones URL de logotipo del sitio web predeterminado. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4. El ID del parche es MDVA-37725. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los correos electrónicos de pedido asincrónico se envían a través de sitios web no predeterminados que contienen las direcciones URL del logotipo del sitio web predeterminado.

<u>Requisitos previos</u>:

1. Se debe haber creado el segundo sitio web, tienda o vista de tienda.
1. La configuración de **Envío asincrónico** debe habilitarse desde **Tiendas** > **Configuración** > **Configuración** > **Ventas** > **Correo electrónico de ventas** > **Configuración general**.
1. La configuración de **Agregar código de tienda a las direcciones URL** está activada para facilitar el acceso al sitio web secundario desde **Tiendas** > **Configuración** > **Configuración** > **Opciones de URL**.

<u>Pasos a seguir</u>:

1. Realice pedidos desde la primera y la segunda tienda.
1. Ejecute cron para enviar los correos electrónicos de ventas.
1. Compruebe el correo electrónico del segundo sitio web.

<u>Resultados esperados</u>:

La URL del logotipo del correo electrónico contiene la URL del segundo sitio web.

<u>Resultados reales</u>:

La URL del logotipo del correo electrónico contiene la URL del sitio web predeterminado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/usage) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
