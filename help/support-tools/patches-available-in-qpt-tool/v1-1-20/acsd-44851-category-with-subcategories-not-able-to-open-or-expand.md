---
title: "ACSD-44851: Categoría con subcategorías que no se pueden abrir o expandir"
description: Este artículo proporciona una solución al problema en el que el usuario no puede abrir o expandir una categoría con subcategorías.
exl-id: 46ad9f9d-ed66-44df-b66d-ab9ff3923c36
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-44851: categoría con subcategorías que no se pueden abrir o expandir

El parche ACSD-44851 resuelve el problema en el que el usuario no puede abrir o expandir una categoría con subcategorías. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 está instalado. El ID del parche es ACSD-44851. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario no puede abrir ni expandir una categoría con subcategorías.

<u>Pasos a seguir</u>:

1. En el Administrador de Adobe Commerce, cree un árbol de categorías con dos categorías raíz y algunas subcategorías para cada una de ellas.
1. Abra la vista o el emulador móvil o reduzca el ancho de la ventana hasta que el diseño se vuelva móvil.
1. Abra el menú principal del catálogo.
1. Intente expandir las categorías raíz.
1. Intente abrir la categoría.

<u>Resultados esperados</u>:

Se puede acceder al menú.

<u>Resultados reales</u>:

El segundo nivel del menú móvil no se abre.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Parches de calidad > Herramientas > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía de la herramienta Parches de calidad.

* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía de la herramienta Parches de calidad.
