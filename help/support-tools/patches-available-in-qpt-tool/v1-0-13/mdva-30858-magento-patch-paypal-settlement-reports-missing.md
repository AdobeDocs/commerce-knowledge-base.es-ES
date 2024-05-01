---
title: "MDVA-30858: Informes de liquidación de PayPal faltantes"
description: '"El parche MDVA-30858 corrige los informes de liquidación de PayPal que faltan cuando se tienen varias cuentas de PayPal. Los informes deben estar disponibles en la barra lateral de administración &gt; **Informes** &gt; Ventas &gt; **Liquidación con PayPal**. En su lugar, el mensaje: * No pudimos encontrar ningún registro.* se muestra. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2".'
exl-id: 268aa74c-5cb5-4653-a6c9-1d4c30167e6a
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# MDVA-30858: Informes de liquidación de PayPal faltantes

El parche MDVA-30858 corrige los informes de liquidación de PayPal que faltan cuando se tienen varias cuentas de PayPal. Los informes deben estar disponibles en la barra lateral de Administración > **Informes** > Ventas > **Liquidación con PayPal**. En su lugar, el mensaje: *No pudimos encontrar ningún registro.* muestra. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 está instalado. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.4

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Corrige el problema por el que no se encontraron registros en **Informes** > Ventas > **Liquidación con PayPal** cuando tengas varias cuentas de PayPal.

<u>Pasos a seguir</u>:

1. Configurar informes de liquidación de PayPal.
1. Vaya a Administración, a **Informes** > Ventas > **Liquidación con PayPal**.
1. Para ver las actualizaciones más recientes, haga clic en **Buscar actualizaciones** en la esquina superior derecha.

<u>Resultados esperados</u>:

Los informes deberían aparecer.

<u>Resultados reales</u>:

No aparece nada en la cuadrícula aunque haya informes disponibles.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
