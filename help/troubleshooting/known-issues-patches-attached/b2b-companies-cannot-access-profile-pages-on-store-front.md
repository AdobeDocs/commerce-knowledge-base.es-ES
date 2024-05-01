---
title: "B2B: Las empresas no pueden acceder a las páginas de perfil en las tiendas"
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.2.4 B2B relacionado con compañías registradas que obtienen errores en sus páginas de cuenta en la tienda.
exl-id: 5f0d81a2-e0a1-487b-8a4f-28b8cb704e32
feature: B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# B2B: Las empresas no pueden acceder a las páginas de perfil en la tienda

Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.2.4 B2B relacionado con compañías registradas que obtienen errores en sus páginas de cuenta en la tienda.

## Problema

Los clientes (empresas) pueden crear correctamente una cuenta de empresa en el sitio, pero obtener la *&quot;No existe esa entidad con customerId =&quot;* y *&quot;Aún no tiene una cuenta de compañía&quot;* mensajes de error. También pueden obtener el *&quot;500 Error interno del servidor&quot;* al intentar acceder a la página Perfil de la compañía.

## Parche

Para descargar el archivo con un parche, haga clic en el siguiente vínculo:

[Descargar MDVA-9013\_EE\_2.2.2\_composer.patch](assets/MDVA-9013_EE_2.2.2_composer.patch.zip)

### Versiones de Adobe Commerce compatibles

El parche se ha creado para:

* Adobe Commerce local 2.2.2

El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce en la infraestructura en la nube de 2.2.0 a 2.2.4
* Adobe Commerce local de 2.2.0 a 2.2.1 y de 2.2.3 a 2.2.4

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obtener instrucciones.
