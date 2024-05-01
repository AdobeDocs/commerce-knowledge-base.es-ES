---
title: "MDVA-23845: no se puede previsualizar la plantilla de correo electrónico cuando la minificación JS está habilitada"
description: El parche del Magento MDVA-23845 corrige el problema al no poder previsualizar la plantilla de correo electrónico en Administración cuando la minificación JS está habilitada.
exl-id: 08579251-a0aa-4e84-9d6a-3fa2999d9c05
feature: Communications, Marketing Tools
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# MDVA-23845: no se puede previsualizar la plantilla de correo electrónico cuando la minificación JS está habilitada

El parche del Magento MDVA-23845 corrige el problema al no poder previsualizar la plantilla de correo electrónico en Administración cuando la minificación JS está habilitada.

Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 está instalado. El ID del parche es MDVA-23845. Tenga en cuenta que el problema se solucionó en la versión 2.3.5 de Magento.

## Productos y versiones afectados

**El parche se crea para la versión de Magento:** Magento Commerce Cloud 2.3.3

**Compatible con versiones de Magento:** Magento Commerce y Commerce Cloud magneto 2.3.2-2.3.4-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir</u> :

1. Activar **Minificación de JS** in **Administración > Tiendas > Configuración > Configuración de JavaScript > Minimizar archivos JavaScript** = *Sí* .
1. Cambie el Magento al modo de producción.
1. Ir a **Administración > Marketing > Comunicaciones > Plantillas de correo electrónico** .
1. Clic **Añadir nueva plantilla** .
1. Seleccione el **Nuevo pedido** plantilla.
1. Haga clic en **Cargar plantilla** botón.
1. Rellenar hacia arriba **Nombre de plantilla** con **Nuevo pedido.**
1. Haga clic en **Guardar plantilla** botón.
1. En la cuadrícula de plantillas de correo electrónico, haga clic en **Previsualizar** vínculo en el **Acciones** columna.

<u>Resultados esperados</u> :

La vista previa de la plantilla de correo electrónico aparece en la ventana emergente abierta, según lo esperado.

<u>Resultados reales</u> :

La vista previa de la plantilla de correo electrónico no aparece en la ventana emergente abierta. La ventana emergente está vacía y pueden aparecer errores de JS.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes enlaces en función del producto de su Magento:

* Magento Commerce: DevDocs [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html) .
* Magento Commerce Cloud: DevDocs [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) .

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) .
* [Comprobar parche para Magento con la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) .

Para obtener más información sobre otros parches disponibles en la herramienta QPT, consulte la [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
