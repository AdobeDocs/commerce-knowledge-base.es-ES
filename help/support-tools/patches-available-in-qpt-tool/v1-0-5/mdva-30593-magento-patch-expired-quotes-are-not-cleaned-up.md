---
title: "Parche de MDVA-30593: las ofertas caducadas no se limpian"
description: El parche MDVA-30593 resuelve el problema en el que las ofertas que caducaron según la configuración **Duración de la cotización** no se limpian. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.3.4.
exl-id: 5ee91546-a5cb-4282-bdfc-c9bb3438af50
feature: Cache, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# Parche de MDVA-30593: las ofertas caducadas no se limpian

El parche MDVA-30593 resuelve el problema en el que las ofertas que caducaron según la configuración de **Duración de la cotización** no se limpian. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.3.4.

## Productos y versiones afectados

* Adobe Commerce (todos los métodos de implementación) 2.3.0-2.3.3.x

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las comillas que caducaron según la configuración de **Duración de la cotización** no se limpian.

<u>Pasos a seguir:</u>

1. En el Administrador de Commerce, vaya a **Tiendas** > **Configuración** > **Ventas** > **Cierre de compra** > **Carro de compras**.
1. Duración de la cotización **establecida (días)** = *1*
1. Guarde la configuración y borre la caché.
1. Inicie sesión como cliente.
1. Añadir un producto al carro de compras.
1. Después de un día, vuelva al carro de compras.

<u>Resultado esperado:</u>

El presupuesto se borra y el producto se elimina del carro de compras, ya que el precio antiguo ya no es válido.

<u>Resultado real:</u>

El producto aún está en el carro de compras.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
