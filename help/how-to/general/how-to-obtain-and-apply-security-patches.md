---
title: Cómo obtener y aplicar [!UICONTROL security patch]
description: Este artículo contiene instrucciones sobre cómo obtener y aplicar una [!UICONTROL security patch] que se ha publicado, pero las instrucciones no están disponibles.
exl-id: 55f2be73-2ccc-4750-a7bd-3058fc2d5107
source-git-commit: b15a1d008b6cc2bdce797768e6ee7029a747e6da
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Cómo obtener y aplicar una [!UICONTROL security patch]

Este artículo contiene instrucciones sobre cómo obtener y aplicar una [!UICONTROL security patch] que se ha publicado, pero las instrucciones no están disponibles.

## Productos y versiones afectados

Adobe Commerce On-Premise y Cloud: todas las versiones

## Causa

Más [!UICONTROL Security Patches] se publican sin ningún archivo físico ni revisión que aplicar.

## Solución


### Caso I:

Si se menciona un archivo de parche o una revisión física en las Notas de la versión:

* Descargue el archivo desde la sección de descarga de [https://account.magento.com](https://account.magento.com/downloads/view/). (En primer lugar, el propietario de la cuenta o el titular de la licencia deben otorgar privilegios de descarga a los usuarios con acceso compartido)

**Advertencias:**

Si tiene una versión anterior de Adobe Commerce y ha adquirido Soporte ampliado, su versión debe ser una de las siguientes para poder aplicar los parches de seguridad:

* 2.4.2-p2
* 2.4.3-p3

Si no tiene soporte ampliado, puede solicitar al soporte técnico que comparta los parches con usted, pero no podrán resolver ningún problema o error que pueda encontrar al aplicarlos.

### Caso II:

Si no se menciona un archivo de parche o una revisión física en las Notas de la versión:

* **Nube:**

1. Algunos [!UICONTROL Security Patches] puede estar incluido/publicado en la última versión de Cloud Tools Suite (ECE Tools) en Cloud Patches para Commerce. Consulte la [Notas de versión](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite)y, si se menciona una corrección de seguridad en la versión, actualice el paquete a esa versión.
1. Si en las Notas de la versión no se menciona una corrección de seguridad, continúe leyendo.

* **Nube o local:**

* Si no hay disponible un archivo/revisión físico, [actualizar la versión de Adobe Commerce en la nube](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) 2.4.X a la última versión de parche 2.4.X-pY.
* Si no hay disponible un archivo/revisión físico, [actualizar la versión de Adobe Commerce local](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) 2.4.X a la última versión de parche 2.4.X-pY.

## Lectura relacionada

* Consulte [Notas de la versión de Commerce Cloud Tools Suite](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) en el *Guía de Adobe Commerce sobre infraestructura en la nube*.
* Consulte [Actualización de la versión de Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) en el *Guía de Adobe Commerce sobre infraestructura en la nube*.
