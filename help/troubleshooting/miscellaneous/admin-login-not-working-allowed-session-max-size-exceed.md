---
title: El inicio de sesión de [!UICONTROL Admin] no funciona - se excedió el tamaño máximo permitido de sesión
description: Solucione el problema cuando intente iniciar sesión en el panel [!UICONTROL Admin], el formulario se actualizará y no podrá hacerlo.
exl-id: 12789df0-6130-4e60-a92a-68ed329bd7fd
source-git-commit: fe4a48581bdfe24da5082b69fb26a8032bd77334
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# El inicio de sesión de [!UICONTROL Admin] no funciona - se excedió el tamaño máximo permitido de sesión

Este artículo proporciona una corrección para los casos en los que intenta iniciar sesión en el panel [!UICONTROL Admin], pero el formulario se actualiza y no puede iniciar sesión, o bien está realizando algunas acciones en el panel [!UICONTROL Admin] y cerró la sesión automáticamente.
Esto se debe a que [!UICONTROL Admin] [!UICONTROL Session Size] se ha excedido.

## Versiones afectadas

* Adobe Commerce local, [todas las versiones compatibles](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce en la infraestructura en la nube, [todas las versiones compatibles](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problema

Experimenta uno de los siguientes síntomas en el [!UICONTROL Admin]:

1. No se puede iniciar sesión en [!UICONTROL Admin] porque el formulario se sigue cargando.
1. Se cerrará la sesión automáticamente al intentar realizar una acción.

## Causa

Se ha superado el tamaño máximo de sesión permitido.

## Solución

Compruebe si hay errores como los siguientes en el archivo `var/log/support_report.log`:

*[2023-07-13T04:26:09.792060+00:00] informe.ADVERTENCIA: El tamaño de la sesión de 260572 superó el tamaño máximo de sesión permitido de 256000. [] []
[2023-07-13T04:26:17.056714+00:00] informe.ADVERTENCIA: El tamaño de sesión de 260570 superó el tamaño máximo de sesión permitido de 256000. [][]*

Si ve estos errores, la solución sería:

<u>Adobe Commerce local</u>:
1. Aumente el valor **[!UICONTROL Max Session Size in Admin]** de la configuración del servidor. Para ello, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Security]** > **[!UICONTROL Max Session Size in Admin]**.
1. Establezca el valor en *500000* o superior. Según el tamaño máximo existente del que se informó en el error, también puede establecer el valor en *0*, lo que eliminará el límite de tamaño de sesión.

<u>Adobe Commerce en la infraestructura en la nube</u>:

(Solo se puede obtener acceso a esta configuración en [!UICONTROL Admin] cuando el modo de implementación/operación es *predeterminado* o *desarrollador*. Sin embargo, solo se permite el modo de implementación de producción en el entorno de la nube).

Para aumentar este valor, ejecute este comando en el terminal (SSH):

```ssh
bin/magento config:set system/security/max_session_size_admin 500000
```

Puede establecer un valor superior a *500000* según el tamaño máximo existente indicado en el error. También puede establecer el valor en *0* para eliminar el límite de tamaño de sesión.

## Lectura relacionada

* [Tamaño de sesión](https://experienceleague.adobe.com/es/docs/commerce-admin/systems/security/security-session-management#admin-sessions) en la Guía de sistemas de administración
* [Modo de operación](https://experienceleague.adobe.com/es/docs/commerce-operations/configuration-guide/cli/set-mode) en la Guía de configuración
* [Conexiones seguras](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/secure-connections) en la Guía de infraestructura de Commerce en la nube
