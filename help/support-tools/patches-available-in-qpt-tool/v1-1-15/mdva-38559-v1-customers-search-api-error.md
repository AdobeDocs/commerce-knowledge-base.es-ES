---
title: "MDVA-38559: /V1/customers/search API devuelve un error"
description: El parche MDVA-38559 soluciona el problema en el que la API /V1/customers/search devuelve un error para los clientes que tienen más de una suscripción. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15. El ID del parche es MDVA-38559. Tenga en cuenta que el problema se corrige en Adobe Commerce 2.4.3.
exl-id: 434fe78c-c384-4fa8-b26a-cb00007e490e
feature: REST, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-38559: /V1/customers/search API devuelve un error

El parche MDVA-38559 corrige el problema en el que la variable `/V1/customers/search` La API devuelve un error para los clientes que tienen más de una suscripción. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 está instalado. El ID del parche es MDVA-38559. Tenga en cuenta que el problema se corrige en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

`/V1/customers/search` La API devuelve un error para los clientes con más de una suscripción.

<u>Requisitos previos</u>:

La tienda Adobe Commerce utiliza más de un sitio web.

<u>Pasos a seguir</u>:

1. Ir a **Almacenar** > **Configuración** > **Cliente** > **Configuración del cliente** > **Opciones de uso compartido de cuentas** y seleccione **Global**.
1. Ir a **Clientes** > **Todos los clientes**, seleccione **Editar** en cualquier cliente y seleccione **Newsletter**.
1. Suscríbase a una newsletter de más de un sitio web y guarde al cliente.
1. Envíe la siguiente solicitud:

```REST API
V1/customers/search?searchCriteria[filterGroups][0][filters][0][field]=email&searchCriteria[filterGroups][0][filters][0][value]=test@example.com&searchCriteria[filterGroups][0][filters][0][conditionType]=eq
```

<u>Resultados esperados</u>:

Se muestran los resultados de búsqueda del cliente.

<u>Resultados reales</u>:

El siguiente error se registra en exception.log: *Ya existe un elemento (Magento\Customer\Model\Customer\Interceptor) con el mismo ID &quot;1&quot;.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
