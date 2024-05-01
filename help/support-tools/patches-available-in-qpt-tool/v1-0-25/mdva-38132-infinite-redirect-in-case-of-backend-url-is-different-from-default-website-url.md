---
title: "MDVA-38132: Redireccionamiento infinito cuando la URL del back-end es diferente de la URL del sitio web predeterminado"
description: El parche MDVA-38132 corrige el problema del redireccionamiento infinito cuando la URL del back-end es diferente de la URL del sitio web predeterminado. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25. El ID del parche es MDVA-38132. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.
exl-id: 122145d7-0961-47f8-8ab6-a15d62996e49
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-38132: redireccionamiento infinito cuando la URL del back-end es diferente de la URL del sitio web predeterminado

El parche MDVA-38132 corrige el problema del redireccionamiento infinito cuando la URL del back-end es diferente de la URL del sitio web predeterminado. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 está instalado. El ID del parche es MDVA-38132. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**
Adobe Commerce en infraestructura en la nube 2.3.4-p2

**Compatible con las versiones de Adobe Commerce:**
Adobe Commerce (todos los métodos de implementación) 2.3.3-2.4.2-p1
>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El panel de administración de Commerce tiene un redireccionamiento infinito cuando la dirección URL del back-end es diferente de la dirección URL del sitio web predeterminado.

<u>Requisitos previos</u>:

* La URL base se usa tanto para el servidor como para la tienda. No se utiliza la URL segura base.
* El servidor web está configurado de modo que Adobe Commerce es accesible a través de dos direcciones URL diferentes. La URL 1 se utiliza para la instalación de Adobe Commerce.

<u>Pasos a seguir</u>:

1. Vaya al Panel de administración > **Tiendas** > **Configuración** > **Web**.
1. Deje la URL base original en la configuración global. Es su URL1.
1. Cambiar al ámbito del sitio web principal.
1. Cambie la URL base por otra URL (consulte las condiciones previas para configurar el servidor web correctamente). Esta es su URL2.
1. Borrar caché (si es necesario y posible).
1. Abra el Panel de administración.

<u>Resultados esperados</u>:

El panel de administración se ha abierto correctamente y se puede navegar por él. La tienda del sitio web principal se ha abierto correctamente y se puede navegar.

<u>Resultados reales</u>:

Se produce una redirección infinita. Adobe Commerce redirige de la URL 1 a la URL 2 y continúa hacia atrás y adelante.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos en función del producto de Adobe Commerce:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en la herramienta QPT, consulte la [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
