---
title: "MDVA-30107: El conmutador de tiendas no funciona como se esperaba"
description: El parche de MDVA-30107 soluciona el problema de que el conmutador de tiendas no funciona como se espera si se utilizan distintas URL básicas para las vistas de tiendas. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5.
exl-id: feaef9ed-615f-4a0a-a7c5-1833f993d27f
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MDVA-30107: El conmutador de tienda no funciona como se esperaba

El parche de MDVA-30107 soluciona el problema de que el conmutador de tiendas no funciona como se espera si se utilizan distintas URL básicas para las vistas de tiendas. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5.

## Productos y versiones afectados

* Adobe Commerce local 2.3.0 - 2.3.5.x
* Adobe Commerce en infraestructura en la nube 2.3.0 - 2.3.5.x

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando un usuario cambia de un almacén a otro mediante el conmutador de almacenes, la solicitud falla si el almacén de destino tiene una dirección URL base diferente.

<u>Pasos a seguir</u>:

1. Cree dos o más tiendas con direcciones URL base diferentes.
1. Ir a una página de categoría en una tienda de cualquiera de esas tiendas.
1. Intente cambiar a la otra tienda con el conmutador de tiendas.

<u>Resultados esperados</u>:

Se le redirigirá a una página similar de la otra tienda.

<u>Resultados reales</u>:

Se le redirigirá a la página principal de la misma tienda.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
