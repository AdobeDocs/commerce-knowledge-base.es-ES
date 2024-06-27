---
title: '[!DNL Admin] el inicio de sesión no funciona - se ha superado el tamaño máximo permitido de sesión'
description: Solucione el problema cuando intente iniciar sesión en su [!DNL Admin] el panel y el formulario se actualizarán y no podrá iniciar sesión.
exl-id: 12789df0-6130-4e60-a92a-68ed329bd7fd
source-git-commit: 8718148f6d9a40c9a71484a7fbc818a626e825e1
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# [!DNL Admin] el inicio de sesión no funciona - se ha superado el tamaño máximo permitido de sesión

Este artículo proporciona una corrección para cuando intente iniciar sesión en su [!DNL Admin] , pero el formulario se actualiza y no puede iniciar sesión. Esto se debe a que [!DNL Admin] Se ha superado el tamaño de la sesión.

## Versiones afectadas

* Adobe Commerce local, [todas las versiones compatibles](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce en la infraestructura en la nube, [todas las versiones compatibles](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problema

Es imposible iniciar sesión en el [!DNL Admin], porque el formulario se sigue recargando.

## Causa

Se ha superado el tamaño máximo de sesión permitido.

## Solución

Compruebe la `var/log/support_report.log` para errores como los siguientes:

*[13-07-2023:26:09.792060+00:00] report.WARNING: El tamaño de sesión de 260572 excedió el tamaño máximo de sesión permitido de 256000. [] []
[13-07-2023:26:17.056714+00:00] report.WARNING: El tamaño de sesión de 260570 excedió el tamaño máximo de sesión permitido de 256000. [][]*

Si ve estos errores, la solución sería:

<u>Adobe Commerce local</u>:
1. Aumente el **[!UICONTROL Max Session Size in Admin]** valor de la configuración back-end. Para ello, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Security]** > **[!UICONTROL Max Session Size in Admin]**.
1. Establezca el valor en *500000* o superior. Según el tamaño máximo existente del que se informe en el error, también puede establecer el valor en *0* lo que elimina el límite de tamaño de sesión.

<u>Adobe Commerce en la infraestructura en la nube</u>:

(A esta configuración solo se puede acceder desde el [!DNL Admin] cuando el modo de implementación/operación es predeterminado para el desarrollador. Sin embargo, solo se permite el modo de implementación de producción en el entorno de nube).

Para aumentar este valor, ejecute este comando en el terminal (SSH):

```ssh
bin/magento config:set system/security/max_session_size_admin 500000
```

Puede establecer como superior a *500000* en función del tamaño máximo existente del informe en el error y también puede establecer el valor en *0* para eliminar el límite de tamaño de sesión.

## Lectura relacionada

* [Tamaño de sesión](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-session-management#admin-sessions) en la Guía de sistemas de administración.
* [Modo de funcionamiento](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/set-mode) en la Guía de configuración.
* [Conexiones seguras](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) en la Guía de infraestructura de Commerce en la nube.
