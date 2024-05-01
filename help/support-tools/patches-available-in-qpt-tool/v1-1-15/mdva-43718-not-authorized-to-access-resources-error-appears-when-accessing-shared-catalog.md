---
title: "MDVA-43718: Aparece el error 'el consumidor no tiene autorización para acceder a los recursos' al acceder al catálogo compartido"
description: La revisión MDVA-43718 resuelve el problema en el que el error *consumidor no tiene autorización para acceder a %recursos.* aparece al acceder a un catálogo compartido desde una integración personalizada. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15. El ID del parche es MDVA-43718. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: fa783ed4-906e-4ee6-b82a-cfe6db5ae89e
feature: Catalog Management
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-43718: Aparece el error &quot;el consumidor no tiene autorización para acceder a los recursos&quot; al acceder al catálogo compartido

El parche MDVA-43718 resuelve el problema donde el error *el consumidor no tiene autorización para acceder a %resources.* aparece al acceder a un catálogo compartido desde una integración personalizada. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 está instalado. El ID del parche es MDVA-43718. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Aparece el siguiente error al acceder a un catálogo compartido desde una integración personalizada: *El consumidor no tiene autorización para acceder a %resources*.

<u>Pasos a seguir</u>:

1. Cree una nueva integración desde Administración > **Sistema** > **Integración** > **Añadir integración**.
1. Añada acceso a los siguientes recursos y active la integración:

   * Magento_SharedCatalog::list
   * Magento_SharedCatalog::manage
   * Magento_Catalog::catalog

1. Uso del acceso de integración: `rest/default/V1/sharedCatalog/1`

<u>Resultados esperados</u>:

Se devuelven los detalles del catálogo compartido.

<u>Resultados reales</u>:

Se devuelve el siguiente error:

```JSON
"message": "The consumer isn't authorized to access %resources.",
"resources": "Magento_SharedCatalog::sharedCatalog"
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
