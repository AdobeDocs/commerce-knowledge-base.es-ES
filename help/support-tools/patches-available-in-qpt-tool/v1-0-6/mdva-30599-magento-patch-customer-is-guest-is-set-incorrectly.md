---
title: 'MDVA-30599: customer_is_guest se ha configurado incorrectamente'
description: El parche MDVA-30599 corrige el problema en el que las comillas de invitado creadas mediante API se marcan incorrectamente como comillas para los clientes que iniciaron sesión. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6. El problema se solucionó en Adobe Commerce 2.4.2.
exl-id: e16bb926-241b-451e-89a5-33000f73c5b7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-30599: customer_is_guest no se ha configurado correctamente

El parche MDVA-30599 corrige el problema en el que las comillas de invitado creadas mediante API se marcan incorrectamente como comillas para los clientes que iniciaron sesión. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6. El problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.5-p2

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.4 - 2.4.0

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las comillas de invitado creadas con API se marcan incorrectamente como comillas para los clientes que iniciaron sesión.

<u>Pasos a seguir</u>:

1. En la tienda de Adobe Commerce, añada un producto al carro de compras como usuario invitado.
1. En la base de datos de Adobe Commerce, busque el(la) `quote_id_mask` correspondiente.
1. Envíe una solicitud de API a la interfaz del repositorio de carro de compras `quoteGuestCartRepositoryV1` para los carros de compras invitados. Se puede realizar mediante una solicitud Swagger o cURL.

```curl
curl -X GET "http://web2-73.sparta.corp.magento.com/dev/support/ee24dev/rest/all/V1/guest-carts/ToOwPtSBxkorkCLq6ztwupPd99y8zhky" -H "accept: application/json"
```

<u>Resultados esperados</u>:

En respuesta recibe `"customer_is_guest": true`

<u>Resultados reales</u>:

En respuesta recibe `"customer_is_guest": false`

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Pasos adicionales necesarios tras la instalación del parche

El parche será efectivo para todos los carros nuevos. Si necesita corregir los carros de invitados existentes, establezca `quote.customer_is_guest = 1` para los registros en los que `quote.customer_id` sea NULL. Puede ejecutar una consulta similar a la siguiente:

```sql
UPDATE quote SET customer_is_guest = 1 WHERE customer_id IS NULL;
```

>[!WARNING]
>
>Se recomienda encarecidamente probar la consulta en el entorno de ensayo/integración antes de ejecutarla en producción. También recomendamos tener una copia de seguridad reciente antes de cualquier manipulación con DB.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
