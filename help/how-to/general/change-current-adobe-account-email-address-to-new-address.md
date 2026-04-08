---
title: Cambiar la dirección de correo electrónico de la cuenta actual de Adobe
description: Aprenda a cambiar la dirección de correo electrónico actual registrada en la cuenta de Adobe a una nueva dirección actualmente no registrada en la cuenta de Adobe o en la cuenta de Magento.
exl-id: ca549d38-0d62-4206-9727-0ed85b733dc3
feature: Communications
source-git-commit: 2fc3353c7563cff6fb82236d40a91306523a579e
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# Cambiar la dirección de correo electrónico de la cuenta actual de Adobe

Este artículo explica cómo cambiar la dirección de correo electrónico actual registrada en la [cuenta de Adobe](https://account.adobe.com/) por una nueva dirección que no esté registrada actualmente en la [cuenta de Adobe](https://account.adobe.com/) o en la [cuenta de Magento](https://account.magento.com/).

## Productos y versiones afectados

* Adobe Commerce (todos los métodos y versiones de implementación)

## Requisitos previos

El propietario de la nueva dirección de correo electrónico debe tener acceso al correo electrónico actual.

Si no tiene acceso a la dirección de correo electrónico actual, configure el reenvío de correo electrónico desde el correo electrónico del propietario actual a un correo electrónico nuevo mediante la configuración del servidor de correo de la empresa.

## Pasos para cambiar la dirección de correo electrónico

Siga estos pasos para cambiar la dirección de correo electrónico:

1. Restablezca la contraseña utilizada con la dirección de correo electrónico anterior. Siga las instrucciones indicadas en [Restablecer contraseña olvidada](https://helpx.adobe.com/es/manage-account/using/change-or-reset-password.html) en la ayuda de Adobe.
1. El vínculo para restablecer la contraseña se envía al buzón del propietario actual con instrucciones.
1. Vaya a la [página de cuenta de Adobe](https://account.adobe.com) para iniciar sesión con el nuevo correo electrónico y configurar la contraseña.

## Importante: El nombre de usuario de la cuenta de Cloud no se actualiza automáticamente

Si usas Adobe Commerce en una infraestructura en la nube, al cambiar la dirección de correo electrónico en tu cuenta de Adobe o el ID de MAGE, no se actualiza automáticamente el nombre de usuario que aparece en tu [cuenta en la nube](https://accounts.magento.cloud).

Después de completar los pasos de este artículo para cambiar la dirección de correo electrónico de la cuenta de Adobe:

1. Inicie sesión en su cuenta de Cloud en [https://accounts.magento.cloud](https://accounts.magento.cloud).
1. Actualice manualmente el perfil de cuenta de Cloud (nombre de usuario) siguiendo los pasos de [Cómo actualizar el perfil de cuenta de Cloud](/help/how-to/general/how-to-update-the-cloud-account-profile.md) en nuestra base de conocimiento de asistencia.

Esto garantiza que el nombre de usuario de su cuenta de Cloud permanezca alineado con el correo electrónico actualizado de Adobe o MAGE ID y evita confusiones al acceder a proyectos en la nube o recibir notificaciones del sistema.

## Verificar el acceso a Marketplace y Asistencia después del cambio de correo electrónico

Después de cambiar la dirección de correo electrónico del ID de MAGE, también debe completar los siguientes pasos para asegurarse de que Adobe Commerce Marketplace and Support reconoce correctamente su nuevo correo electrónico:

### Verificar correo electrónico de Commerce Marketplace

1. Inicie sesión en [https://commercemarketplace.com/customer/account](https://commercemarketplace.com/customer/account) y confirme que el correo electrónico de la cuenta se ha actualizado a la nueva dirección.
1. Si el correo electrónico no se ha actualizado, envíe un [ticket de asistencia](https://experienceleague.adobe.com/es/support#home) solicitando que se corrija el correo electrónico de la cuenta de Commerce Marketplace.

### Pedir al soporte técnico que finalice las actualizaciones de la cuenta interna

1. Envíe un [ticket de asistencia](https://experienceleague.adobe.com/es/support#home) en el que se nos pida que completemos las actualizaciones internas que se requieran (por ejemplo, la actualización del vínculo entre sus ID de Adobe antiguos y nuevos y su ID de MAGE).
1. Si ya ha abierto un ticket de asistencia porque el correo electrónico de Commerce Marketplace no se actualizó en la sección anterior, puede utilizar el mismo ticket para solicitar estas actualizaciones internas adicionales.
