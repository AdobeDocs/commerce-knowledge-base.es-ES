---
title: '"MDVA-41215: Los usuarios reciben un error 500 después de configurar la cookie "mage-messages"'
description: El parche de MDVA-41215 soluciona el problema en el que los usuarios reciben un error 500 después de configurar la cookie "mage-messages" si ya existe, pero no hay mensajes nuevos. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8. El ID del parche es MDVA-41215. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: 93555984-1eed-4866-ab49-5467f9afd124
feature: Configuration
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# MDVA-41215: Los usuarios reciben un error 500 después de configurar la cookie &quot;mage-messages&quot;

El parche de MDVA-41215 soluciona el problema en el que los usuarios reciben un error 500 después de configurar la cookie &quot;mage-messages&quot; si ya existe, pero no hay mensajes nuevos. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 está instalado. El ID del parche es MDVA-41215. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.1

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios obtienen el error 500 después de configurar la cookie &quot;mage-messages&quot; si ya existe, pero no hay mensajes nuevos.

<u>Pasos a seguir</u>:

1. Ir a **../cliente/cuenta/inicio de sesión**.
1. Abra la pestaña de red en las herramientas de desarrollo del explorador (asegúrese de marcar la opción Conservar registro).
1. Rellene el formulario con valores no válidos (el inicio de sesión debe fallar).
1. Clic **Enviar**.
1. Copie como cURL la primera solicitud de la pestaña de red y busque los valores PHPSESSID y form_key.
1. Reemplace los valores PHPSESSID y form_key en la solicitud cURL actualizada y envíela.

```curl -sSL -D - 'http://magento24.loc/customer/account/loginPost/' -i -o /dev/null \
--data-raw 'form_key=i4UVctCCEdAlG13P&login%5Busername%5D=aaa%40bbb.ccc&login%5Bpassword%5D=qwerty' \
--header 'cookie: mage-messages=%5B%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%5D; PHPSESSID=l5575pntrhopuk3ld6maf5aa2m; mage-messages=%5B%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%5D; private_content_version=0de5bf3a3e27e966dd5d6c1ee84e27a7'
```

<u>Resultados esperados</u>:

Los usuarios obtienen `HTTP/1.1 200 OK`

<u>Resultados reales</u>:

Los usuarios obtienen `HTTP/1.1 500 Internal Server Error`

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
