---
title: "MDVA-12304: Error 503 en el frente de la tienda y error de cookie"
description: Este parche de MDVA-12304 Adobe Commerce soluciona errores 503 en los frentes de las tiendas, con *No se puede enviar la cookie. Se superaría el número máximo de cookies.* mensaje de error en los registros. Se trata de un problema conocido de Adobe Commerce 2.2.5. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12.
exl-id: b4b1a2f7-f328-488f-86b8-576b908792fb
feature: Storefront
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# MDVA-12304: Error 503 en el frente de la tienda y error de cookie

Este parche de MDVA-12304 Adobe Commerce soluciona 503 errores en las tiendas, con *No se puede enviar la cookie. Se superaría el número máximo de cookies.* mensaje de error en los registros. Se trata de un problema conocido de Adobe Commerce 2.2.5. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 está instalado.

## Productos y versiones afectados

* **El parche se crea para la versión de Adobe Commerce:** Adobe Commerce local 2.2.5.
* **Compatible con las versiones de Adobe Commerce:** Adobe Commerce (todos los métodos de implementación) 2.x.x.

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los clientes reciben un error 503 al navegar por la tienda. En el `var/log/exception.log` hay el siguiente mensaje de error *No se puede enviar la cookie. Se superaría el número máximo de cookies.*

El problema se produce porque el límite predeterminado de cookies de Adobe Commerce está establecido en 50 y, si el explorador del cliente alcanza el límite, Commerce genera una excepción. La solución proporcionada en el parche aumenta el límite de cookies a 200.

<u>Pasos a seguir:</u>

El error 503 se puede mostrar en cualquier momento cuando el cliente intenta iniciar sesión y ver su carro de compras.

En el `var/log/exception.log` hay el siguiente mensaje de error *No se puede enviar la cookie. Se superaría el número máximo de cookies.*

<u>Resultado real:</u> El cliente no puede comprobar el carro de compras ni completar el pedido.

<u>Resultado esperado:</u> El cliente puede consultar el carro de compras y completar el pedido.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.


## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
