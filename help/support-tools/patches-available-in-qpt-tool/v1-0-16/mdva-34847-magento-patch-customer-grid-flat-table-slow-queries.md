---
title: 'MDVA-34847: customer_grid_plain table - consultas lentas'
description: El parche MDVA-34847 resuelve el problema en el que las consultas lentas se producen en la tabla customer_grid_plain. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16. Tenga en cuenta que el problema se corrigió en la versión 2.4.3 de Adobe Commerce.
exl-id: e91cb86d-83cd-4267-a132-64465a57da7f
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-34847: consultas lentas de tabla customer_grid_plain

El parche MDVA-34847 resuelve el problema de las consultas lentas en la `customer_grid_flat` tabla. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 está instalado. Tenga en cuenta que el problema se corrigió en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.3

**Compatible con las versiones de Adobe:**

Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.0 - 2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las consultas lentas se producen en `customer_grid_flat` tabla.

<u>Pasos a seguir</u>:

1. Crear un usuario administrador con un ámbito personalizado (Ejemplo: Set) **GWS** = *0,* y elija el sitio web predeterminado existente con **ID** = *1*).
1. Cree cualquier producto y elemento de categoría.
1. Realice un pedido desde el front-end.
1. Inicie sesión en el administrador como el nuevo usuario.
1. Vaya a la cuadrícula de ventas (**Ventas > Pedidos**).
1. Compruebe que la consulta SQL se haya enviado a la base de datos (base de datos).

<u>Resultados esperados</u>:

La extensión GWS de administrador debe utilizar

```sql
int
```

valores de

```sql
website_id
```

en condiciones SQL, como se espera, como:

```sql
main_table.website_id IN (1)
```

<u>Resultados reales</u>:

La extensión de GWS de administrador agregó una condición con

```sql
website_id
```

valor como

```sql
string
```

, como:

```sql
main_table.website_id IN ('1')
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
