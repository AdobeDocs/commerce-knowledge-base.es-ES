---
title: "Parche de MDVA-22150 Adobe Commerce: el usuario de front-end no puede iniciar sesión"
description: El parche MDVA-22150 resuelve el problema cuando un usuario de front-end no puede iniciar sesión después de una compra anulada con un cupón. Esto ocurre cuando un usuario de front-end utiliza un código de cupón en un producto que se ha deshabilitado antes de completar la compra. El resultado es que el usuario de front-end ya no puede iniciar sesión y recibe un error 503. Otro efecto de este problema es que la capacidad de administrar los carros de compras de los clientes en el Administrador deja de funcionar.
exl-id: 8aabe7b2-4b8a-4339-914e-7131006907b3
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# Parche de MDVA-22150 Adobe Commerce: el usuario de front-end no puede iniciar sesión

El parche MDVA-22150 resuelve el problema cuando un usuario de front-end no puede iniciar sesión después de una compra anulada con un cupón. Esto ocurre cuando un usuario de front-end utiliza un código de cupón en un producto que se ha deshabilitado antes de completar la compra. El resultado es que el usuario de front-end ya no puede iniciar sesión y recibe un error 503. Otro efecto de este problema es que la capacidad de administrar los carros de compras de los clientes en el Administrador deja de funcionar.

Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13. Tenga en cuenta que el problema se corrigió en la versión 2.3.4 de Adobe Commerce.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:** Adobe Commerce en la infraestructura en la nube 2.3.2

**Compatible con versiones de Adobe Commerce:** Adobe Commerce en infraestructura en la nube y Adobe Commerce 2.3.1 - 2.3.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir:</u>

1. Inicie sesión en Admin y cree un producto configurable.
1. Vaya a **Reglas del carro de compras** y cree un código de cupón con algún descuento.
1. Cree una cuenta de cliente en el front-end.
1. Añada el producto al carro de compras, siga el proceso de cierre de compra e introduzca el cupón.
1. Después de introducir el cupón, no envíe la solicitud, sino que aborte la solicitud y cierre la sesión.
1. Vuelva al Administrador y deshabilite todo el producto configurable.

<u>Resultados esperados:</u>

El producto no se muestra en el carro de compras de la Tienda, o se muestra con el mensaje de error correspondiente de que el producto se ha deshabilitado, según lo esperado.

<u>Resultados reales:</u>

* Al intentar volver a iniciar sesión en el front-end, se quedará atascado en un bucle infinito (que finalmente mostrará una excepción después de un largo período de tiempo).
* La capacidad de administrar los carros de compras de los clientes en el Administrador deja de funcionar.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
