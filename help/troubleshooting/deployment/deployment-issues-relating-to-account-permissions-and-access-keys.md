---
title: Problemas de implementación relacionados con los permisos de cuenta y las claves de acceso
description: Este artículo proporciona una solución para los problemas relacionados con la implementación de Adobe Commerce en la infraestructura en la nube causados por conflictos de propiedad de claves de acceso.
exl-id: e8d72ebe-453f-4d18-a25e-c76e685aa667
feature: Deploy, Roles/Permissions
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: e439352c-5b67-587d-b34e-d2a0aa5a0242
    internal-label: Roles/Permissions
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%
---
# Problemas de implementación relacionados con los permisos de cuenta y las claves de acceso

Este artículo proporciona una solución para los problemas relacionados con la implementación de Adobe Commerce en la infraestructura en la nube causados por conflictos de propiedad de claves de acceso.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, todas las versiones compatibles

## Problema

<u>Requisitos previos</u>:

La licencia de Cloud está asociada al contacto A (dirección de correo electrónico: *<u>first@e.mail</u>*)

<u>Pasos a seguir</u>:

1. Contacto A creó las claves de acceso de Adobe Commerce en su cuenta (clave X) y las instaló en la nube.
1. El contacto B (dirección de correo electrónico: *<u>second@e.mail</u>*) compró una extensión con su cuenta y creó las claves de acceso para instalar la extensión (clave Y).
1. El contacto A abandonó la empresa y la licencia (propiedad) se transfirió al contacto B.
1. El integrador de sistemas intenta instalar la extensión en el entorno de la nube con la clave X.

<u>Resultado esperado</u>:

Extensión instalada correctamente.

<u>Resultado real</u>:

La extensión no está instalada porque la implementación falla.

## Causa

Ambas claves se asignan a la función de contacto, lo que provoca un conflicto.

## Solución

Si se produce un error en una implementación después de realizar un cambio en el contacto principal de la cuenta (con la cuenta original y la nueva cuenta, cada una con sus propias claves de acceso) y las claves se han transferido de la cuenta original a la nueva cuenta, debe deshabilitar las claves de la cuenta original. En cuanto al ejemplo anterior, la clave X debe desactivarse.

### Cómo deshabilitar la clave de acceso

Si no tiene acceso a la cuenta de [Commerce Marketplace](https://marketplace.magento.com/) asociada con la clave antigua, [póngase en contacto con el servicio de asistencia de Adobe Commerce](https://experienceleague.adobe.com/es/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) para deshabilitar la clave.

Si tiene acceso a la cuenta de Marketplace asociada con la clave antigua, realice los siguientes pasos para deshabilitar la clave:

1. Inicie sesión en [Commerce Marketplace](https://marketplace.magento.com/) con las credenciales de la cuenta anterior.
1. Haga clic en el nombre de la cuenta en la parte superior derecha de la página y seleccione **Mi perfil**.
1. Haga clic en **Claves de acceso** en la ficha Marketplace.

   ![magento_products_access_keys_2.4.1.png](/help/troubleshooting/miscellaneous/assets/magento_products_access_keys_2.4.1.png)

1. Haga clic en **Deshabilitar** junto a la clave de acceso.

## Lectura relacionada

* [Obtenga sus claves de autenticación](https://experienceleague.adobe.com/es/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) en nuestra documentación para desarrolladores.
