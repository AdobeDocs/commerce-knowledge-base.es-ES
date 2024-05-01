---
title: "Parche de MDVA-31759: la importación de CSV ignora las actualizaciones de atributos"
description: El parche MDVA-31759 corrige el problema en el que la importación de CSV ignora los atributos adicionales con tipos *Dropdown* y *Text Area*. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.
exl-id: 5426866c-893f-4abe-bfbc-6e7b30dd8dab
feature: Attributes, Data Import/Export
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# Parche de MDVA-31759: la importación de CSV ignora las actualizaciones de atributos

El parche MDVA-31759 soluciona el problema de que la importación de CSV ignora los atributos adicionales de *Desplegable* y *Área de texto* tipos. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 está instalado. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.4.0

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.0 - 2.4.1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La importación de CSV ignora los atributos adicionales con *Desplegable* y *Área de texto* tipos.

<u>Pasos a seguir</u>:

1. Inicie sesión en el administrador de Commerce.
1. Cree un atributo de producto con la configuración siguiente:
   * **Etiqueta predeterminada**: *G003*
   * **Tipo de entrada de catálogo del propietario de la tienda**: *Área de texto* o *Desplegable*
   * **Código de atributo**: *G003*
   * **Ámbito**: *Global*
1. Agregue el atributo anterior al conjunto de atributos predeterminado.
1. Cree un producto con el conjunto de atributos predeterminado y especifique un valor para el nuevo atributo.
1. Exporte el producto a CSV.
1. Actualice el valor del atributo en **additional\_attributes** columna.
1. Importe el CSV actualizado.

<u>Resultados esperados</u>:

Se actualiza el valor del atributo G003.

<u>Resultados reales</u>:

El valor del atributo G003 no se ha actualizado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
