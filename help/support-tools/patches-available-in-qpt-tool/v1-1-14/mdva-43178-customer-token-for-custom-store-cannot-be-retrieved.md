---
title: "MDVA-43178: El token de cliente para la tienda personalizada no se puede recuperar en GraphQL"
description: El parche MDVA-43178 corrige el problema en el que el token de cliente para una tienda personalizada no se puede recuperar en GraphQL. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14. El ID del parche es MDVA-43178. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: b2a8bf96-7534-41d2-b83b-58d8e0b6d076
feature: GraphQL
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-43178: el token de cliente para la tienda personalizada no se puede recuperar en GraphQL

El parche MDVA-43178 corrige el problema en el que el token de cliente para una tienda personalizada no se puede recuperar en GraphQL. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 está instalado. El ID del parche es MDVA-43178. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El token de cliente de una tienda personalizada no se puede recuperar en GraphQL.

<u>Pasos a seguir</u>:

1. Cree dos vistas de tienda para la tienda predeterminada.
1. Crear un sitio web, una tienda y una vista de tienda nuevos. Asigne a esta vista de tienda el nombre &quot;test3&quot;.
1. Cree un cliente para el nuevo sitio web.
1. Generar token de administración de API:

   `http://domain/rest/all/V1/integration/admin/token`

   <pre>
    <code class="language-graphql">
    {
      "username": "login",
      "password": "password"
    }
    </code>
    </pre>

1. Envíe GraphQL para recuperar el token de cliente como administrador y utilice el token de administrador para la autorización. En el encabezado, &quot;store&quot; = &quot;test3&quot;:

   <pre>
    <customer_email>
      </pre>

<u>Resultados esperados</u>:

Se genera el token del cliente.

<u>Resultados reales</u>:

No se ha generado el token de cliente. Los comerciantes obtienen *El correo electrónico del cliente proporcionado no existe* en respuesta.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
