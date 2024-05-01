---
title: "ACSD-46703: La función de arrastrar y soltar para personalizar el producto no funciona"
description: Este artículo proporciona una solución al problema en el que las opciones personalizables de producto de arrastrar y soltar no funcionan según lo esperado.
exl-id: 49b29495-d225-4f34-ac76-b7294a86aea6
feature: Products
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-46703: La función de arrastrar y soltar para personalizar el producto no funciona

El parche ACSD-46703 corrige el problema en el que las opciones personalizables del producto (arrastrar y soltar) no funcionan según lo esperado. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 está instalado. El ID del parche es ACSD-46703. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.5

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [Herramienta Parches de calidad] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios no pueden arrastrar y soltar las opciones personalizables de una página a otra.

<u>Pasos a seguir</u>:

1. Cree un producto sencillo.
1. Añada opciones personalizables al producto simple y asegúrese de añadir más de 20 opciones que resulten en paginación.
1. Intente mover una opción personalizable (arrastrar y soltar) dentro de la misma página.
1. Ahora intente mover una opción personalizable de la página dos a la página uno.

<u>Resultados esperados</u>:

* Puede arrastrar y soltar las opciones personalizables de una página a otra.
* Puede ordenar los valores mediante la funcionalidad de arrastrar y soltar, incluso para varias páginas.

<u>Resultados reales</u>:

No puede mover ningún valor a otra página mediante la funcionalidad de arrastrar y soltar.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Parches de calidad > Herramientas > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía de la herramienta Parches de calidad.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía de la herramienta Parches de calidad.
