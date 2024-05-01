---
title: Comprobar parche para el problema de Adobe Commerce con la herramienta Parches de calidad
description: Este artículo proporciona información general sobre la herramienta Parches de calidad (QPT) y vínculos a recursos que explican cómo utilizarla.
exl-id: 43393708-3939-449f-a764-b2ac6326165f
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Comprobar parche para el problema de Adobe Commerce con la herramienta Parches de calidad

Este artículo proporciona información general sobre la herramienta Parches de calidad (QPT) y vínculos a recursos que explican cómo utilizarla.

## Productos y versiones afectados

* Adobe Commerce local, todo [versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Adobe Commerce en la infraestructura en la nube, todo [versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Qué es la herramienta Parches de calidad

El [Herramienta Parches de calidad](https://github.com/magento/quality-patches) (QPT) son parches individuales desarrollados por el Adobe y la comunidad de Magento Open Source.

Le permite hacer lo siguiente:

* aplicar parches de calidad incluidos en el paquete
* revertir parches aplicados anteriormente
* consulte la información general sobre parches de calidad disponibles para la versión instalada de Adobe Commerce.

Este es un ejemplo de la tabla de estado que puede obtener para ver los parches disponibles:

![Magento_parches_lista](assets/status_table.png)

La herramienta está diseñada para permitirle autoabastecerse con parches para problemas que pueda experimentar con Adobe Commerce o aplicar fácilmente los parches sugeridos por el soporte de Adobe Commerce.

>[!NOTE]
>
>QPT es solo para parches de calidad. Los parches de seguridad están disponibles en [Centro de seguridad de Magento](https://magento.com/security/patches).

## Parches disponibles en la herramienta Parches de calidad

Consulte la [Herramienta Parches de calidad](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores para obtener la lista de parches disponibles.

## Cómo instalar y utilizar la herramienta Parches de calidad

Los comandos de instalación y uso son diferentes para Adobe Commerce local y para Adobe Commerce en la infraestructura en la nube, ya que para la nube el paquete QPT se incluye en el paquete ece-tools.

### Cómo instalar y utilizar QPT para Adobe Commerce local

Consulte la [Guía de actualización de software > Parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores para obtener detalles sobre cómo instalar y utilizar QPT para aplicar y revertir parches.

### Cómo instalar y utilizar QPT para Adobe Commerce en la infraestructura en la nube

Consulte la [Cloud for Adobe Commerce > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores para obtener más información sobre cómo instalar y utilizar QPT para aplicar y revertir parches en Adobe Commerce en la infraestructura en la nube.

## Lectura relacionada

* [Notas de la versión de Parches de calidad](https://devdocs.magento.com/quality-patches/release-notes.html) en nuestra documentación para desarrolladores.
* [Cómo aplicar los parches del compositor proporcionados por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de soporte.
