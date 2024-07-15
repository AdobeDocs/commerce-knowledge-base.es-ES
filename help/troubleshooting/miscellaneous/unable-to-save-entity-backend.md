---
title: No se puede guardar el backend de Adobe Commerce de entidad
description: Este artículo proporciona una solución para los casos en los que no pueda guardar una entidad en el backend de Adobe Commerce. Por ejemplo, cuando no puede editar ni guardar una regla "cart_price" específica.
exl-id: e45dc88a-2da0-4524-bd61-6634cfebb169
feature: Admin Workspace, Marketing Tools
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# No se puede guardar el backend de Adobe Commerce de entidad

Este artículo proporciona una solución para los casos en los que no pueda guardar una entidad en el backend de Adobe Commerce. Por ejemplo, cuando no puede editar ni guardar una regla `cart_price` específica.

## Productos y versiones afectados

Este problema puede afectar a todas las versiones de Adobe Commerce que tienen configurado el tamaño máximo de sesión. Se agregó a partir del Magento Open Source 2.3.7-p1 y comercio de Adobe (todos los métodos de implementación) 2.4.3.


## Problema

Al intentar reconfigurar la tienda, la página se vuelve a cargar y los cambios no se guardan. Se puede ver un mensaje en `var/log/system.log`:

*[2021-11-27 00:30:52] informe.ADVERTENCIA: el tamaño de la sesión de 418056 superó el tamaño máximo de sesión permitido de 256000. [][]*

<u>Pasos a seguir</u>:

Un ejemplo de configuración de tienda que no se guarda:

1. Seleccione una regla en la tienda Adobe Commerce en Producción > **Marketing** > **Reglas de precio del carro de compras**.
1. Elija una regla y establézcala en *Inactiva* y guarde el cambio.

<u>Resultado esperado</u>:

La regla se establece en inactiva.

<u>Resultado real</u>:

* La página se vuelve a cargar sin ningún mensaje.
* La regla sigue configurada como activa.

## Causa

Este problema está relacionado con la nueva funcionalidad introducida recientemente que ha afectado al tamaño máximo de sesión. Consulte [Administración de sesiones](https://docs.magento.com/user-guide/stores/security-session-management.html) en nuestra documentación para desarrolladores.

## Solución

Aumente el valor &quot;Tamaño máximo de sesión&quot; en (**Almacenes** > **Configuración** > **Avanzado** > **Sistema** > **Seguridad** > Tamaño máximo de sesión).

## Lectura relacionada

* [Menú de mercadotecnia](https://docs.magento.com/user-guide/marketing/marketing-menu.html) en nuestra guía del usuario.
