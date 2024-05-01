---
title: Solución de problemas de bloqueo de cuenta de Adobe Commerce Intelligence
description: Este artículo proporciona soluciones para el bloqueo de cuentas de Adobe Commerce Intelligence. Primero tendremos que determinar si se trata de un defecto, un fallo temporal o algo más. Seguir los pasos a continuación le ayudará a volver a su cuenta lo antes posible.
exl-id: 85968257-ba4b-4cfb-a4fa-497b4c5b5aea
feature: Cache, Commerce Intelligence, Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---

# Solución de problemas de bloqueo de cuenta de Adobe Commerce Intelligence

<!--
BOB: Is this in TOC?
-->

Este artículo proporciona soluciones para el bloqueo de cuentas de Commerce Intelligence. Primero tendremos que determinar si se trata de un defecto, un fallo temporal o algo más. Seguir los pasos a continuación le ayudará a volver a su cuenta lo antes posible.

## Verifique que su dirección de correo electrónico sea correcta

Compruebe su dirección de correo electrónico para asegurarse de que la dirección de correo electrónico que intenta utilizar para iniciar sesión esté asociada a una cuenta de Commerce Intelligence existente. Es posible que tenga que pedir al administrador de una cuenta que confirme que no hay errores tipográficos en la dirección de correo electrónico.

Una vez que haya confirmado que la dirección de correo electrónico es correcta, intente iniciar sesión de nuevo utilizando [este vínculo](https://dashboard.rjmetrics.com/v2/session/create#/).

## Intente restablecer la contraseña

Si ha comprobado que está utilizando el correo electrónico correcto, intente restablecer la contraseña. Puede usar el complemento **¿Olvidaste?** en la página de inicio de sesión de la sección anterior para almacenar en déclencheur un correo electrónico de restablecimiento de contraseña.

Si no ve el correo electrónico al principio, asegúrese de buscar en la carpeta de correo electrónico no deseado. A veces, incluso los correos electrónicos bien intencionados se pueden confundir con basura. **Tenga en cuenta que los vínculos de acceso temporal en estos correos electrónicos solo son válidos una vez.**

Si sigues bloqueado, asegúrate de que tu dirección de correo electrónico sea correcta y que estés usando el enlace correcto del correo electrónico que restableciste. Recomendamos probar lo siguiente **antes de solicitar otro restablecimiento e intentar iniciar sesión de nuevo:**

* Borre la caché, las cookies y las contraseñas guardadas del explorador
* Desactivar temporalmente cualquier software de bloqueo de anuncios

## Documente los errores y póngase en contacto con el servicio de asistencia

>[!NOTE]
>
>Este paso no siempre es necesario, pero completarlo de forma proactiva podría reducir el tiempo empleado en ir y venir en una solicitud de asistencia.

Si sigue sin poder acceder a su cuenta, le recomendamos que compruebe si hay errores y que envíe un ticket a nuestro equipo de asistencia. ¿Cómo puedes hacer esto? Abra las herramientas para desarrolladores del explorador y realice una captura de pantalla de los errores mostrados en la consola o en la ventana de registro del sitio. En el GIF siguiente, estoy abriendo las herramientas para desarrolladores de Google Chrome:

![Abra las herramientas para desarrolladores de Chrome.](assets/Opening_Chrome_dev_tools.gif)

En el ejemplo anterior, se ha utilizado el método más común (**clic derecho** > **Inspect**) para abrir la consola. Si su navegador no tiene este método o necesita ayuda, utilice los siguientes enlaces de documentación para el navegador web que está utilizando:

<table>
<tbody>
<tr>
<td><a href="https://www.technipages.com/mac-os-x-enable-web-inspector-in-safari">Safari</a></td>
<td><a href="https://developer.mozilla.org/en-US/docs/Tools/Web_Console/Opening_the_Web_Console">Firefox</a></td>
<td><a href="https://developers.google.com/web/tools/chrome-devtools/?hl=en">Chrome</a></td>
<td><a href="https://www.opera.com/dragonfly/documentation/">Opera</a></td>
<td><a href="https://msdn.microsoft.com/en-us/library/gg589512(v=vs.85).aspx#OpeningTools">Internet Explorer</a></td>
</tr>
</tbody>
</table>

En algunos exploradores, es posible que al abrir las herramientas para desarrolladores no se muestre automáticamente la consola; es posible que primero se muestre el código del sitio. Si esto le sucede, haga clic en la opción Console de la ventana del desarrollador y realice capturas de pantalla de los errores que se muestran allí.

Envíe un ticket a nuestro equipo de asistencia con el **capturas de pantalla con errores** y su **Dirección de correo electrónico de la cuenta de Commerce Intelligence**.

## ¿No ves ningún error o simplemente estás perdido?

¡No te preocupes! Presenta un nuevo ticket de soporte (asegúrate de incluir la dirección de correo electrónico de tu cuenta de Commerce Intelligence) y te devolveremos a tu cuenta lo antes posible.

## Temas relacionados en nuestra base de conocimiento de soporte:

* [Adición de un nuevo usuario y configuración de permisos](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/administrator/user-mgmt/user-management.html)
* [¿Cómo actualizo mi dirección de correo electrónico o contraseña?](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/administrator/user-mgmt/create-user.html)
* [¿Cómo puedo restablecer mi contraseña?](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/administrator/user-mgmt/reset-password.html)
