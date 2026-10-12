---
title: No se puede iniciar sesión en la asistencia de Adobe Commerce o en la cuenta de la nube
description: Este artículo proporciona una solución para cuando tenga problemas para iniciar sesión en la asistencia de Adobe Commerce o en su proyecto de nube.
exl-id: 676b32d2-8197-4c60-a1b1-3c51b01dd3a3
feature: Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '276'
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

Se le redirige a una página para iniciar sesión con una cuenta de Adobe y las credenciales no funcionan.

![adobe-login-two](assets/adobe-login-two.png)


## Causa

Como parte de nuestro proceso de integración de Adobe Commerce con otras soluciones de Adobe, todos los usuarios deberán crear un inicio de sesión de Adobe, si aún no lo tienen, utilizando la misma dirección de correo electrónico conectada a su MageID.

## Solución

Puede iniciar sesión en la cuenta con:

- Una cuenta corporativa/personal de Adobe existente.
- Si no tiene una cuenta de Adobe, cree una con la misma dirección de correo electrónico.

Para ver los pasos, consulte [Commerce Identity Manager](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-identity-manager.html?lang=es) en Adobe Experience League.

## Lectura relacionada

- [Vínculo Magento.com e inicios de sesión en la cuenta de accounts.magento.cloud](/help/faq/general/linking-magento-com-and-accounts-magento-cloud-account-logins.md)
