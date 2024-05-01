---
title: "MDVA-35312: la solicitud de GraphQL vacía genera un error 500, no 200 OK"
description: El parche MDVA-35312 corrige el problema en el que una solicitud vacía de GraphQL genera un código de respuesta de error 500. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18. El ID del parche es MDVA-35312. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.
exl-id: 345fdbd4-8a43-4aab-a318-72792c8a7a78
feature: GraphQL
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# MDVA-35312: la solicitud de GraphQL vacía genera un error 500, no 200 OK

El parche MDVA-35312 corrige el problema en el que una solicitud vacía de GraphQL genera un código de respuesta de error 500. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 está instalado. El ID del parche es MDVA-35312. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se crea para la versión de Magento:**

Adobe Commerce en infraestructura en la nube 2.4.2

**Compatible con versiones de Magento:**

Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.4.1-p1-2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Una solicitud de GraphQL vacía genera un código de respuesta de error 500 en lugar de un código 200.

<u>Pasos a seguir</u>:

Envíe una solicitud de GraphQL, por ejemplo:

```curl
curl -i -X OPTIONS http://inv.test/graphql
```

<u>Resultados esperados</u>:

Respuesta: *200 OK*.

<u>Resultados reales</u>:

Respuesta: *Error interno del servidor HTTP/1.1 500*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
