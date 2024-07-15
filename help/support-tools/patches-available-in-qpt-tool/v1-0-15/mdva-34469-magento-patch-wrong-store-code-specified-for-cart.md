---
title: "MDVA-34469: Código de tienda incorrecto especificado para el carro de compras"
description: "El parche de MDVA-34469 soluciona el problema en el que los usuarios reciben el mensaje de error: *Código de tienda incorrecto especificado para el carro de compras* al añadir un producto al carro de compras después de cambiar de vista de la tienda. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15. El ID del parche es MDVA-34469. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2."
exl-id: 35d4f120-7fcf-4996-8b23-aca99cfc18ac
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-34469: código de tienda incorrecto especificado para el carro de compras

El parche MDVA-34469 soluciona el problema en el que los usuarios reciben el mensaje de error: *Código de tienda incorrecto especificado para el carro de compras* al agregar un producto al carro de compras después de cambiar de vista de la tienda. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15. El ID del parche es MDVA-34469. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce en la infraestructura en la nube 2.4.1

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.4.1 - 2.4.1-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario ve un error en la consulta del carro de compras, *&quot;Se especificó un código de almacén incorrecto para el carro de compras&quot;*, al intentar cambiar las vistas de la tienda.

<u>Requisitos previos</u>:

* Adobe Commerce 2.4.0.
* Se configura un solo sitio web con una sola tienda y dos vistas de tienda.
* Se crea una cuenta de cliente.

<u>Pasos a seguir</u>:

1. El back-end de Adobe Commerce está configurado para tener dos vistas de tienda (con códigos de tienda: predeterminado, segundo).
1. El usuario crea un carro de compras con el código de tienda predeterminado.
1. El usuario intenta recuperar este carro utilizando el segundo código de almacén en el encabezado de la solicitud `Store`.

<u>Resultados esperados</u>:

Se muestra el carro de compras porque al cambiar de tienda (y enviar el nuevo código en el encabezado de solicitud de `Store`) se asocia el carro de compras al almacén solicitado.

<u>Resultados reales</u>:

La consulta del carro de compras devuelve un error y no se muestra.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
