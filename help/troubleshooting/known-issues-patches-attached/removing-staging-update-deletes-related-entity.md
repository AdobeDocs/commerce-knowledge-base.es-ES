---
title: Al eliminar la actualización de ensayo se elimina la entidad relacionada
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.2.3 relacionado con la entidad (categoría, página de CMS, etc.) que se elimina cuando se elimina la actualización de programación relacionada.
exl-id: 91138ac1-916e-4dd1-bad5-892524fdd9e1
feature: CMS, Cache, Categories, Staging
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# Al eliminar la actualización de ensayo se elimina la entidad relacionada

Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.2.3 relacionado con la entidad (categoría, página de CMS, etc.) que se elimina cuando se elimina la actualización de programación relacionada.

>[!NOTE]
>
>El problema se solucionó en Adobe Commerce 2.2.6.

## Problema

Cuando se elimina una actualización de programación activa entre sus fechas de inicio y finalización, también se elimina la entidad relacionada (categoría, subcategoría, página de CMS).

<u>Pasos a seguir (con categorías)</u>:

1. Inicie sesión en el administrador de Commerce.
1. Cree una nueva subcategoría en **Catálogo** > **Categorías**.
1. Cree una nueva actualización de ensayo con la hora de inicio y finalización.
1. Espere hasta que se aplique la actualización; ese es el momento de inicio.
1. Elimine la actualización con el **Ver/Editar** vínculo.

<u>Resultados esperados</u>:

La actualización se elimina y la subcategoría sigue existiendo en el administrador.

<u>Resultados reales</u>:

Se eliminan la actualización y la subcategoría.

## Solución

Aplique el parche proporcionado en este artículo y limpie la caché en ejecución

```bash
bin/magento
  cache:clean
```

## Parche

Los parches se adjuntan a este artículo. Para descargar un parche, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el vínculo correspondiente:

* [Descargar MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-11059_EE_2.2.3_COMPOSER_v1.patch.zip)
* [Descargar MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch](assets/MDVA-23505_EE_2.2.4_COMPOSER_v1.patch.zip)
* [Descargar MDVA-12158\_EE\_2.2.5\_COMPOSER\_v2.patch](assets/MDVA-12158_EE_2.2.5_COMPOSER_v2.patch.zip)

### Versiones de Adobe Commerce compatibles:

Los parches se han creado para:

* MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch se ha creado para Adobe Commerce (todos los métodos de implementación) 2.2.3
* MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch se ha creado para Adobe Commerce (todos los métodos de implementación) 2.2.4
* MDVA-12158\_EE\_2.2.5\_COMPOSER\_v2.patch se ha creado para Adobe Commerce (todos los métodos de implementación) 2.2.5

El parche de MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce local 2.2.0-2.2.2
* Adobe Commerce en la infraestructura en la nube 2.2.0-2.2.3

El parche de MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce local 2.1.0-2.1.18, 2.2.0-2.2.3
* Adobe Commerce en infraestructura en la nube 2.1.0-2.1.18, 2.2.0-2.2.3

El parche de MDVA-23505\_EE\_2.2.5\_COMPOSER\_v1.patch también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce en la infraestructura en la nube 2.2.5

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obtener instrucciones.

## Archivos adjuntos
