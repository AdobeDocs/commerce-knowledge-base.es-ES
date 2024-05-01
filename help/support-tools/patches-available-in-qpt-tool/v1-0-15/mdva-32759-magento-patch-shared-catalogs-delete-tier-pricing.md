---
title: "MDVA-32759 patch: los catálogos compartidos eliminan los precios de los niveles"
description: El parche MDVA-32759 soluciona el problema de los catálogos compartidos que eliminan los precios de nivel existentes.
exl-id: c6192d2f-cd25-483e-ba69-01ca62996faf
feature: B2B, Catalog Management
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Parche MDVA-32759: los catálogos compartidos eliminan los precios de los niveles

El parche MDVA-32759 soluciona el problema de los catálogos compartidos que eliminan los precios de nivel existentes.

Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 está instalado. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.4-p2

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.0 - 2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Requisitos previos</u>:

Instale Adobe Commerce con B2B, con **Funciones B2B** activado.

<u>Pasos a seguir</u>:

1. Ir a **Tiendas > Configuración > Funciones B2B > Habilitar compañía** y **Catálogo compartido**.
1. Ejecutar `bin/magento cron:run`.
1. Cree un producto sencillo y haga clic en **Precios avanzados** y agregue. **Precio de catálogo y de nivel** y, a continuación, guárdelo.
1. Ir a **Catálogo > Catálogo compartido > Definir precios y estructura**, haga clic en **Configurar** y en ese menú desplegable, anule la selección de todas las opciones y guarde.
1. Ejecutar `bin/magento cron:run`.
1. Abra el producto creado anteriormente y consulte los precios avanzados.

<u>Resultados esperados</u>:

Los precios de nivel no deben eliminarse de los productos después de eliminar todos los productos del catálogo compartido público, como se espera.

<u>Resultados reales</u>:

Los precios del nivel se eliminan después de eliminar todos los productos del catálogo compartido público.


## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
