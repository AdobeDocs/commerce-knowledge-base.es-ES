---
title: '''ACSD-48313: [!UICONTROL configurable_variations] columna no analizada si el valor del atributo contiene coma'
description: Aplique el parche ACSD-48313 para solucionar el problema de Adobe Commerce donde la variable [!UICONTROL configurable_variations] no se analiza si el valor del atributo contiene una coma.
exl-id: 0ac3f8da-4da3-4308-bea4-98a5b6926b0d
feature: Attributes, Configuration
role: Admin
source-git-commit: 4cb43c4f16238253fc7fc75d9af9b921dfa74158
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-48313: **[!UICONTROL configurable_variations]** la columna no se analiza si el valor del atributo contiene una coma

El parche ACSD-48313 resuelve el problema donde **[!UICONTROL configurable_variations]** no se analiza si el valor del atributo contiene una coma. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 está instalado. El ID del parche es ACSD-48313. La versión en la que se solucionará este problema aún no está disponible.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con las versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.4-p5

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Después de exportar productos configurables, el archivo resultante no se puede importar de nuevo debido a un problema de formato con el **[!UICONTROL configurable_variations]** atributo. Esto sucede cuando hay opciones de atributo que incluyen una coma.

<u>Pasos a seguir</u>:

1. Ir a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** y cree un nuevo atributo _Tamaño_:
1. Tipo de entrada de catálogo para el propietario de la tienda: **[!UICONTROL Dropdown]**.
1. Cree opciones que incluyan una coma, p. ej.:
   * 10,2 cm.
   * 15,5 cm.
1. **[!UICONTROL Advanced Attribute Properties]** - Ámbito: _Global_.
1. Cree un nuevo producto configurable con la funcionalidad Crear configuraciones.
1. Seleccione el atributo anterior _Tamaño_ y las dos opciones que incluyen la coma.
1. Ir a **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** y cree una nueva exportación de productos (ejecute el cron para almacenar en déclencheur la generación del archivo CSV).
1. Ir a **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** e intente volver a importar el mismo archivo CSV creado anteriormente.

<u>Resultados esperados</u>:

El usuario debe poder importar el archivo.

<u>Resultados reales</u>:

```
1. Column configurable_variations: Attribute with code "2cm" does not exist or is missing from product attribute set in row(s): 3
2. Column configurable_variations: Attribute with code "5cm" does not exist or is missing from product attribute set in row(s): 3
3. Column configurable_variations: Invalid option value for attribute "size" in row(s): 3
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.


## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
