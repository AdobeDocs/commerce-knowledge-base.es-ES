---
title: No se puede iniciar sesión en la asistencia de Adobe Commerce o en la cuenta de la nube
description: Este artículo proporciona una solución para cuando tenga problemas para iniciar sesión en la asistencia de Adobe Commerce o en su proyecto de nube.
exl-id: 676b32d2-8197-4c60-a1b1-3c51b01dd3a3
feature: Cloud, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# No se puede iniciar sesión en la asistencia de Adobe Commerce o en la cuenta de la nube

Este artículo proporciona una solución para cuando tenga problemas para iniciar sesión en la asistencia de Adobe Commerce o en su proyecto de nube.

## Productos y versiones afectados

Adobe Commerce (todos los métodos de implementación) [todas las versiones compatibles](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problema

Al ir a [https://account.magento.com/customer/account/login/](https://account.magento.com/customer/account/login/) o [https://accounts.magento.cloud/user](https://accounts.magento.cloud/user), es posible que observe que ahora hay un formulario de inicio de sesión unificado y que ya no puede escribir sus credenciales como lo había hecho anteriormente.

<u>Pasos a seguir</u>:

Intente iniciar sesión en su cuenta de Commerce.

![adobe-login-one](assets/adobe-login-one.png)

<u>Resultado esperado</u>:

Inicio de sesión correcto.

<u>Resultado real</u>:

Se le redirige a una página para iniciar sesión con una cuenta Adobe y las credenciales no funcionan.

![adobe-login-two](assets/adobe-login-two.png)


## Causa

Como parte de nuestro proceso de integración de Adobe Commerce con otras soluciones de Adobe, todos los usuarios deberán crear un inicio de sesión de Adobe, si aún no lo tienen, utilizando la misma dirección de correo electrónico conectada a su MageID.

## Solución

Puede iniciar sesión en la cuenta con:

- Cuenta personal/corporativa de Adobe existente.
- Si no tiene una cuenta Adobe, cree una con la misma dirección de correo electrónico.

Para ver los pasos, consulte [Commerce Identity Manager](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-identity-manager.html) en Adobe Experience League.

## Lectura relacionada

- [Vínculo Magento.com e inicios de sesión en la cuenta de accounts.magento.cloud](/help/faq/general/linking-magento-com-and-accounts-magento-cloud-account-logins.md)
