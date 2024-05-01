---
title: 'ACSD-48857: No se pueden guardar los cambios después de editar con [!DNL Page Builder]'
description: Aplique el parche ACSD-48857 para solucionar el problema de Adobe Commerce en el que el usuario no puede guardar los cambios después de editar con [!DNL Page Builder].
exl-id: c95b354d-8954-4e9c-9e92-8a64f62f0a68
feature: Admin Workspace, CMS, Page Builder
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-48857: no se pueden guardar los cambios después de editar con [!DNL Page Builder]

El parche ACSD-48857 corrige el problema en el que el usuario no puede guardar los cambios después de editar con [!DNL Page Builder]. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 está instalado. El ID del parche es ACSD-48857. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario no puede guardar los cambios después de editar con [!DNL Page Builder].

<u>Pasos a seguir</u>

1. Inicie sesión en el sitio web del administrador.
1. Vaya a **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** para crear una página de CMS vacía.
1. Ejecute este script SQL para establecer lo siguiente **[!UICONTROL Content]** valor de campo:

   ```SQL
   update cms_page set content = '<div data-content-type="text" data-appearance="default" data-element="main"><h4 style="text-align: center;" contenteditable="true" data-placeholder="Edit Heading Text" data-content-type="heading" data-appearance="default" data-element="main">THE RULES</h4></div>' where page_id=8;
   ```

1. Volver a **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** en Administración.
1. Edite la página.
1. Vaya a la **[!UICONTROL Content]** pestaña.
1. Clic **[!UICONTROL Save]**.

<u>Resultados esperados</u>

Se ha implementado la limpieza del contenido del HTML. Esto elimina [!DNL Page Builder] atributos de HTML reservados en el contenido generado por el editor de texto.

<u>Resultados reales</u>

La página permanece sin guardar y el cargador sigue girando. En la consola, se genera el siguiente error:

```
[ERROR] Page Builder was rendering for 5 seconds without releasing locks.
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
