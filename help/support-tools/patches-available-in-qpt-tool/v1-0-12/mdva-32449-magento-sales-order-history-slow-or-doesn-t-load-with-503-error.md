---
title: "MDVA-32449: el historial de pedidos de ventas es lento o no se carga con un error 503"
description: El parche de MDVA-32449 soluciona el problema de Adobe Commerce donde el historial de pedidos de venta se carga lentamente o no se carga y muestra un error 503. Este es un problema cuando los clientes 13000+ se asignan a una compañía B2B. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12. Tenga en cuenta que este problema se solucionó en Adobe Commerce 2.4.1.
exl-id: e3fd4db2-b706-4712-ba8e-270eaca7fdb2
feature: B2B, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-32449: el historial de pedidos de ventas es lento o no se carga con un error 503

El parche de MDVA-32449 soluciona el problema de Adobe Commerce donde el historial de pedidos de venta se carga lentamente o no se carga y muestra un error 503. Este es un problema cuando los clientes 13000+ se asignan a una compañía B2B. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 está instalado. Tenga en cuenta que este problema se solucionó en Adobe Commerce 2.4.1.

## Productos y versiones afectados

Este es un problema cuando los clientes 13000+ se asignan a una compañía B2B.

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en la infraestructura en la nube 2.4.1

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce en la infraestructura en la nube y Adobe Commerce local 2.3.0: 2.3.5-p2, 2.4.0, 2.4.1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Corrige el problema en el que el historial de pedidos se carga muy lentamente o no se carga en absoluto.

<u>Requisitos previos</u>:

13000+ clientes asignados a una empresa B2B

<u>Pasos a seguir</u>:

1. Inicie sesión en la tienda como administrador de la empresa.
1. Ir a la página del historial de pedidos de ventas.

<u>Resultados esperados</u>:

La página del historial de pedidos de venta se carga normalmente.

<u>Resultados reales</u>:

La página se carga muy lentamente o es posible que la página no se cargue y se muestre un error de tiempo de espera.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
