---
title: No se puede acceder a la cuenta o el proyecto de Adobe Commerce correctos o no se encuentra en la cuenta
description: Este artículo proporciona una corrección del problema cuando no puede acceder al proyecto correcto de Adobe Commerce en la nube cuando hay cambios en la propiedad o en las direcciones de correo electrónico.
exl-id: 165b9a18-6e84-4f0f-b377-a07152d55c9e
hide: true
hidefromtoc: true
feature: Cloud, Paas
role: Developer
source-git-commit: 423a392eb32df69c38b84081ac2ed17ae1efdc7b
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# No se puede acceder a la cuenta o al proyecto de nube correcto o el proyecto no está en la cuenta

Este artículo proporciona una corrección para los siguientes problemas después de realizar un cambio en la propiedad de la cuenta o en las direcciones de correo electrónico asociadas:

1. No puede acceder a los proyectos de Cloud Adobe Commerce correctos.
1. No se muestran proyectos de Cloud Adobe Commerce en su cuenta en [accounts.magento.cloud/user](https://accounts.magento.cloud/user).
1. Está viendo los detalles de otra cuenta (es decir, el propietario de la cuenta anterior) en [accounts.magento.cloud/user](https://accounts.magento.cloud/user).

## Problema

No puede acceder al proyecto de Adobe Commerce en la nube correcto cuando hay cambios en la propiedad o en las direcciones de correo electrónico.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, [todas las versiones compatibles](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Causa

Este problema suele ocurrir cuando el inicio de sesión único (SSO) del propietario del proyecto anterior sigue integrado con Adobe.com después de:

1. Se le ha transferido la propiedad del proyecto en la nube a usted (el usuario) y verá la cuenta del propietario del proyecto original. Haga clic aquí para la [solución](#solution-for-cause-one-and-two).

   O

1. Usted (el usuario) se ha trasladado a otra empresa, junto con un cambio en la dirección de correo electrónico y en los proyectos a los que tiene acceso. Verá los proyectos a los que se le había concedido acceso en su función o compañía anterior. Haga clic aquí para la [solución](#solution-for-cause-one-and-two).

   O

1. Ha cambiado su dirección de correo electrónico en https://account.adobe.com a otra dirección de correo electrónico que no está asociada actualmente a un proyecto en la nube. Haga clic aquí para la [solución](#solution-for-cause-three).

## Solución para la causa uno y dos {#solution-for-cause-one-and-two}

La solución para cuando el problema se debe a uno y dos es desconectar la integración de inicio de sesión único con Adobe.com. Siga los pasos a continuación para desconectarse:

1. En https://accounts.magento.cloud/user, expanda la sección **[!UICONTROL Single Sign-On]**. Haga clic en **[!UICONTROL Disconnect from Adobe.com]** para desconectarse.

   ![inicio de sesión único-adobe-connect](assets/sso-adobe-disconnect.png)

1. Haga clic en **[!UICONTROL Disconnect]**.

   ![adobe-desconectar](assets/adobe-disconnect.png)

1. Cerrar sesión.
1. Haga clic en el botón **[!UICONTROL Adobe.com]**.

   ![Magento.com](assets/adobe-welcome-login.png)

1. Ahora debería poder ver la cuenta correcta y acceder al proyecto de nube correcto.

## Solución para la causa tres {#solution-for-cause-three}

Si el problema se ha debido a la causa tres, pida a un superusuario del proyecto que añada su nueva dirección de correo electrónico al proyecto. Para obtener más información, consulte [Administrar acceso de usuario](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html).
