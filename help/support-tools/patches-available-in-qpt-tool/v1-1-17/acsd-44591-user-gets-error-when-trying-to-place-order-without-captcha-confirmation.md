---
title: "ACSD-44591: Errores al realizar el pedido sin confirmación CAPTCHA"
description: El parche ACSD-44591 resuelve el problema en el que el usuario obtiene errores al intentar realizar un pedido sin confirmación CAPTCHA.
exl-id: 5459aa14-dcba-474d-aafa-e4cc73daafbc
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-44591: Errores al realizar un pedido sin confirmación de CAPTCHA

El parche ACSD-44591 resuelve el problema en el que el usuario obtiene errores al intentar realizar un pedido sin confirmación CAPTCHA.
Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 está instalado. El ID del parche es ACSD-44591. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario recibe errores al intentar realizar un pedido sin confirmación CAPTCHA.

<u>Pasos a seguir</u>:

1. Configure el Google ReCaptcha v2 (no soy un robot).
1. Active ReCaptcha para el cierre de compra.
1. Intente realizar un pedido sin hacer clic en ReCaptcha.
1. Una vez que reciba el mensaje de error por la falta de ReCaptcha (*Error de validación de ReCaptcha, vuelva a intentarlo*), haga clic en **ReCaptcha** y luego intente hacer un pedido.

<u>Resultados esperados</u>:

El pedido no se realizará con un ReCaptcha incorrecto.

<u>Resultados reales</u>:

Se obtienen los siguientes errores:

* *Error de validación de ReCaptcha, vuelva a intentarlo*
* *No existe ese carro con id = 1*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
