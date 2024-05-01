---
title: "ACSD-51853: Los estilos de texto copiados no se aplican mediante el generador de páginas"
description: Aplique el parche ACSD-51853 para solucionar el problema de Adobe Commerce donde los estilos de texto copiados no se aplican cuando se utiliza page builder.
feature: Page Builder
role: Admin
exl-id: 1efd3147-1ae0-468b-af04-1632fbaaefda
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-51853: los estilos de texto copiados no se aplican mediante el generador de páginas

El parche ACSD-51853 corrige el problema de que los estilos de texto copiados no se aplican cuando se utiliza el generador de páginas. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.34 está instalado. El ID del parche es ACSD-51853. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los estilos de texto copiados no se aplican cuando se utiliza Page Builder

<u>Pasos a seguir</u>:

1. Inicie sesión en Admin.
1. Vaya a > **content** > **páginas** > **Abra cualquier página** > **Editar con Page Builder**.
1. Arrastrar fila y *Texto* de **[!UICONTROL Elements]**.
1. Copiar **contenido enriquecido**, pegue ese texto en una **[!UICONTROL Page Builder]**.

<u>Resultados esperados</u>

El texto copiado se pega con todos los estilos.

<u>Resultados reales</u>

El texto copiado se pega como texto sin formato y se pierden todos los estilos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
