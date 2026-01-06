---
title: Guía del usuario de asistencia de Experience League para Adobe Commerce
description: Obtenga información sobre cómo enviar un vale de soporte al Soporte de Experience League, proporcionar acceso compartido a las cuentas de y navegar por la Base de conocimiento de Adobe Commerce.
exl-id: 9eb4814f-c9c4-4dd0-b68a-87d712898aa5
feature: Support, Roles/Permissions, Tools and External Services, Admin Workspace, Iaas, Marketing Tools
source-git-commit: dc47ce82fbde398f7379c26e3e911ee086ff363f
workflow-type: tm+mt
source-wordcount: '3095'
ht-degree: 0%

---

# Guía del usuario de asistencia de Experience League para Adobe Commerce

En esta guía, aprenderá a enviar un ticket de asistencia a [Soporte técnico de Experience League](https://experienceleague.adobe.com/home?lang=es#support) y a proporcionar acceso compartido a las cuentas de Adobe Commerce.

>[!NOTE]
>
>La asistencia de Adobe Commerce ha migrado del Centro de ayuda de Adobe Commerce a Experience League. Utilice el flujo de formulario de casos de Experience League descrito [aquí](#what-is-experience-support) para enviar casos de soporte técnico.

>[!NOTE]
>
>En este momento, para ver los casos que ha enviado anteriormente en el Centro de ayuda de Adobe Commerce, debe ir a https://support.magento.com/hc/en-us/requests, ya que estos casos no se han migrado al nuevo sistema de tickets de asistencia. El Centro de ayuda es ahora de solo lectura; para seguir recibiendo ayuda para el problema original, tendrás que enviar un ticket de seguimiento a [Soporte técnico de Experience League](https://experienceleague.adobe.com/home?lang=es#support).

>[!NOTE]
>
>La parte de la Base de conocimiento del Centro de ayuda de Adobe Commerce se ha migrado al portal de Adobe Experience League. Al crear un ticket de asistencia, se le sugerirán artículos de la Base de conocimiento relacionados, junto con otra documentación de Adobe Commerce relevante de Adobe Experience League.

**Actualización importante:** 29 de julio de 2024

**[¿QUÉ ES COMPATIBILIDAD CON EXPERIENCE LEAGUE?](#what-is-experience-support)**

**[CASOS DE SOPORTE TÉCNICO](#support-cases)**

* [Iniciar sesión en Soporte de Experience League](#sign-in-experience-support)
* [Envío de un caso de asistencia](#support-case)

   * [Página de inicio de Adobe Experience League](#experience-league-start-page)
   * [página de cuenta de Adobe Commerce](#submit-case-adobe-commerce-account-page)
   * [*Verifique su dirección de correo electrónico*](#verify-email-address-error)

* [Seguimiento de los casos de asistencia](#track-support-cases)
* [Comentarios en su caso](#comments-in-your-case)
* [Cierre su caso](#close-case)
* [Vuelva a abrir el caso](#reopen-case)
* [Enviar ticket mediante la consola de Cloud](#cloud-console)
* [Línea directa de Adobe Commerce P1](#P1-hotline)
* [Modelo operativo de responsabilidad compartida de Adobe Commerce](#shared-responsibility-operational-model)

**[ACCESO COMPARTIDO: CONCEDA PRIVILEGIOS PARA QUE OTROS USUARIOS TENGAN ACCESO A SU CUENTA](#shared-access)**

* [Quién puede proporcionar acceso compartido](#who-can-provide-shared-access)
* [Proporcionar acceso compartido](#provide-shared-access)
* [Revocar (eliminar) el acceso compartido](#revoke-shared-access)

   * [¿Cómo eliminar a los usuarios a los que se les concedió acceso compartido a través de un proyecto de Cloud?](#remove-cloud-shared-access-users)

* [Acceso a una cuenta compartida (cuentas de conmutador)](#switch-accounts)
* [Solución de problemas de acceso compartido](#troubleshooting-shared-access)

**[PREGUNTAS FRECUENTES SOBRE FACTURACIÓN PARA ADOBE COMMERCE](#billing-faq)**


## ¿QUÉ ES COMPATIBILIDAD CON EXPERIENCE LEAGUE? {#what-is-experience-support}

Soporte de Experience League es un portal de soporte para Adobe donde los clientes de Adobe Commerce aptos pueden enviar y administrar vales de soporte. También es donde puede revisar los artículos de resolución de problemas.

## CASOS DE SOPORTE {#support-cases}

La administración de casos de soporte de Adobe Experience League permite trabajar con el soporte a través de casos para abordar problemas específicos encontrados al utilizar productos de Adobe, incluido Adobe Commerce, para todos los productos de Adobe Commerce bajo contrato.

## INICIAR SESIÓN EN ASISTENCIA DE EXPERIENCE LEAGUE {#sign-in-experience-support}

El inicio de sesión le permite enviar, actualizar y responder a preguntas de los agentes en vales de soporte.

Para iniciar sesión en la asistencia de Adobe Experience League, siga estos pasos:

1. Vaya a [experienceLeague.adobe.com](https://experienceleague.adobe.com/es).
1. Inicie sesión con sus credenciales de inicio de sesión de Adobe.

![iniciar sesión en experience-league](assets/experience_league_sign_in.png)

### Envío de un caso de asistencia {#support-case}

Una vez que haya iniciado sesión correctamente como propietario de la cuenta o usuario de acceso compartido, puede enviar un caso de asistencia técnica mediante la página de inicio de Adobe Experience League, la página de la cuenta de Adobe Commerce y la página de la cuenta de Adobe Commerce Cloud.

>[!NOTE]
>
>Las solicitudes de soporte para el equipo de Adobe Commerce Marketplace no se pueden enviar a través de Experience League, ya que su sistema de soporte funciona en una plataforma independiente que no está integrada con Experience League.
>
>Puede enviar su caso de soporte si las siguientes afirmaciones son verdaderas:
>
>* La organización en cuestión recibe el nombre en la columna izquierda y termina en ([!DNL Commerce]). El problema está relacionado con esa organización o una cuenta asociada con ella.
>* El problema es que no puede iniciar sesión en la cuenta de Marketplace o que tiene alguna pregunta acerca de la implementación de una extensión.
>* Tu problema no es solo solicitar un reembolso por tus compras en Marketplace.
>
>Para problemas relacionados con la publicación de su extensión, problemas para comprar o solicitar un reembolso en [Adobe Commerce Marketplace](https://commercemarketplace.adobe.com/), debe ponerse en contacto directamente con el equipo de [!DNL Commerce Marketplace] visitando https://commercemarketplace.adobe.com/. Vaya a la parte inferior de la página y haga clic en **[!UICONTROL Contact Us]**, que abrirá un formulario para enviar un ticket de asistencia de Marketplace.

#### Página de inicio de Adobe Experience League {#experience-league-start-page}

Para enviar un nuevo caso de asistencia técnica mediante la página de inicio de Adobe Experience League, siga estos pasos:

>[!INFO]
>
>1. Para enviar un caso, debe tener derecho a recibir asistencia para el producto correspondiente (por ejemplo, Adobe Commerce, Adobe Commerce Intelligence, Adobe Commerce Payment Services, Experience Platform, etc.). Si no tiene derecho a asistencia, aparecerá una barra en la parte superior de la página que le informará de que no es un usuario con derecho a asistencia en la organización.
>1. Si pertenece a varias organizaciones o hay varias con nombres de aspecto similar (cada una representará a cualquiera de los demás productos de Adobe a los que la organización tiene suscripciones), primero deberá seleccionar la organización adecuada en el menú desplegable de la columna izquierda que termina en *[!DNL (Commerce)]*.
>1. Si la lista desplegable **[!UICONTROL Select a product]** está vacía al enviar un caso, es probable que esté usando una cuenta de socio de Adobe Commerce. Solo los usuarios con [acceso compartido](#shared-access) de un comerciante con derechos de asistencia pueden enviar tickets. Para problemas de comerciantes, solicite acceso compartido. Para problemas de socios, póngase en contacto con spphelp@adobe.com.

>[!NOTE]
>
>Asegúrese de haber seleccionado la organización correcta antes de enviar el caso y de que la organización seleccionada tiene los derechos adecuados para el producto para el que solicita asistencia. Por ejemplo, si su problema está relacionado con Adobe Commerce, pero ha seleccionado Adobe Commerce Intelligence o Adobe Experience Platform como producto y el caso se ha enviado correctamente, esto puede provocar un enrutamiento incorrecto del caso y retrasos en los tiempos de respuesta.
>
>Además, si se seleccionó la organización incorrecta en el momento en que se envió el caso, su equipo no podrá ver el caso en [!UICONTROL My Cases] para la organización correcta o adecuada. El equipo de Soporte de Adobe Commerce no tiene la capacidad de cambiar la organización asociada con el caso; para solucionar esto, debe cerrar el caso existente y enviar un nuevo caso con los detalles apropiados proporcionados/seleccionados.

1. Haz clic en **Asistencia** en el encabezado. Se abrirá la página de inicio de Asistencia.

   ![página de soporte técnico abierta](assets/commerce_support_homepage.png)

1. Para comenzar el proceso de admisión de asistencia, asegúrese de haber seleccionado la organización adecuada en la lista desplegable Organización (si está visible). Para enviar un caso para Adobe Commerce, seleccione el nombre de la organización que termina en *[!DNL Commerce]*.

   ![select_proper_org](assets/select_appropriate_org.png)

1. Haga clic en **[!UICONTROL Open Ticket]** en el menú de la izquierda o haga clic en **[!UICONTROL Get Started]** en la tarjeta *[!UICONTROL Open a support ticket]*.

   ![caso de soporte abierto](assets/open_support_case.png)

1. Seleccione un producto del menú desplegable y proporcione un título y una descripción para el caso. NOTA: Si la lista desplegable no muestra ningún producto o [!DNL Commerce] no es una opción disponible, intente cambiar [!UICONTROL Organization] en la columna izquierda y vuelva a comprobarlo.

   ![seleccionar_producto](assets/support_case_product.png)

   >[!NOTE]
   >
   >Si envía un ticket con &quot;**[!DNL Commerce]en la infraestructura en la nube**&quot; seleccionado como producto y la organización tiene varios proyectos enumerados, se le pedirá que seleccione el [!UICONTROL Project ID] apropiado. Si no puede encontrar el(la) [!UICONTROL Project ID] deseado(a), asegúrese de agregar una nota en el ticket que indique que está buscando ayuda con un &quot;proyecto X&quot; diferente.<br>Si tiene intención de enviar un ticket de &quot;**[!DNL Commerce]en Managed Services**&quot; y está en **[!DNL Commerce]en la infraestructura en la nube**, pero no ve **[!DNL Commerce]en la infraestructura en la nube** como un producto disponible:<br>1. Escriba un asunto para el problema en **[!UICONTROL Case title]**.<br>2. Escriba una descripción de su problema en **[!UICONTROL Case description]**.<br>3. Después de ingresar ambos elementos, se le mostrará el campo **[!UICONTROL Cloud Project URL]** a continuación.


1. Adobe Experience League sugerirá artículos y prácticas recomendadas que pueden ayudarle a resolver su caso. Si todavía necesita soporte directo, deberá proporcionar información adicional antes de enviar su caso.

   ![direct_support_required](assets/direct_support.png)

1. Una vez que haya completado toda la información requerida, haga clic en **[!UICONTROL Submit case]**.

>[!IMPORTANT]
>
>Si no puede ver su organización en el menú desplegable de la organización al iniciar sesión en experienceleague.adobe.com, es posible que tenga que sincronizar su perfil con accounts.magento.com antes de solicitar asistencia técnica o administrar un caso de asistencia existente.
>
>1. Vaya a accounts.magento.com e inicie sesión con el mismo perfil (corporativo, escolar o personal) que utilizará para administrar los casos de asistencia en Adobe Experience League.
>1. Una vez que haya iniciado sesión correctamente en su perfil de accounts.magento.com, vuelva a experienceleague.adobe.com e inicie sesión.
>1. Seleccione su organización en el menú desplegable de organización.
>1. Si su organización sigue sin aparecer, póngase en contacto con el administrador de Commerce para obtener derechos de delegado de asistencia. Para obtener más información, consulte el artículo de ayuda [Uso compartido de cuentas de Commerce](https://experienceleague.adobe.com/es/docs/commerce-admin/start/commerce-account/commerce-account-share).

>[!NOTE]
>
>Por qué es importante la organización o el producto
>
>**Ejemplo A**: solo ha compartido el acceso a una compañía y esa compañía tiene derechos para dos productos de Adobe: Product1 y Product2.
>
>1. Dado que cada organización representa un producto, verá dos organizaciones en el menú desplegable, por ejemplo, OrgA-Product1 y OrgB-Product2.
>1. Si seleccionó Product = Product1 pero el problema está relacionado con Product2, el caso se redirigirá al servicio de asistencia de Product2 y habrá retrasos al transferir el caso al servicio de asistencia de Product1.
>1. Si envió el caso para OrgA-Product1 y desea revisar [!UICONTROL My Cases] para esa organización en el futuro, no lo verá si selecciona OrgA-Product2 como organización (solo tendrá que seleccionar la otra organización, en comparación con el ejemplo B).
>
>**Ejemplo B**: tiene acceso compartido a dos compañías y cada compañía solo tiene derechos para Adobe Commerce.
>
>1. Si ha enviado el caso para la organización A pero el problema realmente afecta a la organización B, los miembros de la organización B no podrán ver este caso en [!UICONTROL My Cases] en el futuro.
>1. Además, los miembros de la organización A podrán ver los casos de menos de [!UICONTROL My Cases] que en realidad están pensados para la organización B, lo que puede conllevar problemas de privacidad.

Debe tener una cuenta en https://account.adobe.com y https://account.magento.com para iniciar sesión en Experience League y enviar un caso de asistencia. No podrá enviar un caso de asistencia hasta que haya iniciado sesión.

>[!NOTE]
>
>Si ya tiene una cuenta en https://account.magento.com pero no puede iniciar sesión, es posible que no se haya registrado para obtener una cuenta en https://account.adobe.com, lo cual es obligatorio a partir de agosto de 2022.
>
>Para resolver esto:
>
>1. Cree una cuenta en https://account.adobe.com con la misma dirección de correo electrónico en su MAG ID.
>1. Vaya a https://account.magento.com para vincular su Adobe ID con el ID de MAG.

#### página de cuenta de Adobe Commerce {#submit-case-adobe-commerce-account-page}

Para enviar un nuevo ticket de asistencia técnica utilizando la página de cuenta de Adobe Commerce, siga estos pasos:

1. Inicie sesión en su cuenta de Adobe Commerce. Consulte [instrucciones detalladas](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-create.html?lang=es#create-a-commerce-account) en nuestra guía de usuario.
1. Haga clic en la ficha **Asistencia**.

   ![pestaña magento_account_support](assets/magento_account_support_tab.png){width="800"}

1. La página de asistencia de Adobe Experience League se carga automáticamente.
1. Seleccione **[!UICONTROL Open Ticket]** en el menú de la izquierda.
1. Rellene [los campos](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/faq/support-ticket-contact-reason-descriptions).
1. Haga clic en **Enviar**.

#### *Compruebe su dirección de correo electrónico* error en la página de cuenta de Adobe Commerce {#verify-email-address-error}

No podrás enviar un ticket de asistencia si recibes el error Comprueba tu dirección de correo electrónico de forma similar a la que se muestra a continuación en la página [Cuenta de Adobe Commerce](https://account.magento.com/).

![Error_Verificar_Dirección_Correo_Electrónico](assets/Verify_Email_Address_Error.png)


### Seguimiento de los casos de asistencia de Commerce {#track-support-case}

Sus casos de soporte son los que usted:

* se ha enviado personalmente.
* se han agregado a como observador mediante un CC (copia de carbón).

>[!NOTE]
>
>Si tiene casos de asistencia técnica que se enviaron con otros productos de Adobe además de Commerce, esos tickets no se pueden rastrear desde la misma pantalla. Primero debe cambiar a la organización asociada con la asignación del producto.
>Por ejemplo, anteriormente seleccionó la organización que termina en &quot;(Commerce)&quot; para rastrear su caso de Commerce, mientras que también tiene casos de asistencia de AEP; esos casos no se mostrarán aquí.

#### Ver sus casos

Puede ver los casos de Commerce que ha enviado personalmente al hacer clic en **[!UICONTROL My Cases]** en el menú de la izquierda. Asegúrese de haber seleccionado la organización correcta que termina en &quot;(Commerce)&quot;.

![casos de compatibilidad de vista](assets/view_support_cases.png)

#### Consulte los casos históricos en el Centro de ayuda de Adobe Commerce

Obtenga más información sobre cómo **ver sus casos históricos** en el Centro de ayuda de Adobe Commerce en [Retirada del Centro de ayuda de Adobe Commerce](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/news/decommissioning-of-adobe-commerce-help-center) en nuestra Base de conocimiento de Adobe Commerce.

#### Vea sus casos observados

Puede ver los casos de Commerce en los que se le ha *agregado como observador* al hacer clic en **[!UICONTROL My organization's cases]** en el menú de la izquierda.

<!-- TODO: Add image here -->


#### Búsqueda de casos

Para encontrar casos, escriba su consulta de búsqueda en el campo *[!UICONTROL Search]* y presione *intro* en el teclado.

![search-cases](assets/search_cases.png)

#### Escalar sus casos

Si cree que un caso requiere más atención y ha pasado nuestro tiempo de respuesta inicial, puede escalar el caso. Para ello,

1. Haga clic en **[!UICONTROL Escalate to management]** en la parte inferior derecha del panel *[!UICONTROL Case Detail]*, en la parte derecha de la pantalla.

   ![escalar a administración](assets/escalate_to_management.png)

1. Después de hacer clic en, aparecerá un formulario emergente. Complete el formulario y haga clic en **[!UICONTROL Escalate]**.

   ![confirmar-escalación](assets/confirm_escalation.png)

   *Las razones para la escalación pueden incluir*: habilidades de comunicación del agente, conocimientos técnicos del agente, espera de devolución/actualización, cambio en la urgencia del problema, la resolución no cumplió con las expectativas o tiempo para la resolución.

#### Añadir un observador en los casos de asistencia

Puede agregar observadores para admitir los casos enviados por los miembros de su organización. Los observadores recibirán notificaciones por correo electrónico cuando se envíen nuevos casos o se actualicen los casos existentes.

1. Para añadir un observador a un caso existente, abra el caso y haga clic en el icono de lápiz situado junto a &quot;observadores&quot; en el panel Detalles del caso, en la parte derecha de la pantalla.

   ![observadores de complementos](assets/add_watchers.png)

1. Después de hacer clic en el lápiz, puede agregar o quitar observadores de la lista.

   ![observadores de actualizaciones](assets/update_watchers.png)

>[!NOTE]
>
>Para obtener más información sobre cómo agregar y quitar observadores para su caso, vea el vídeo [Agregar y quitar observadores, cerrar y volver a abrir vales](https://experienceleague.adobe.com/es/docs/commerce-learn/tutorials/help-and-support/add-remove-watchers-close-reopen-support-ticket).

### Comentarios en su caso {#comments-in-your-case}

Los comentarios de su caso contienen todos los comentarios escritos por usted o por el equipo de asistencia de Adobe Commerce. Los comentarios se muestran de los más recientes (arriba) a los más antiguos (abajo).
Para añadir un comentario, siga estos pasos:

1. Desplácese hasta la parte inferior del ticket.
1. Escriba su comentario en el campo **[!UICONTROL Comments]** y haga clic en **[!UICONTROL Add comments]**.

![add-comments](assets/add_comments.png)

### Cierre su caso {#close-case}

Para cerrar el caso, haga clic en **[!UICONTROL Close case]** en la parte inferior derecha del panel *[!UICONTROL Case Detail]*.

![close-case](assets/close_case.png)

>[!NOTE]
>
>Para obtener más información sobre cómo cerrar el caso, consulte el vídeo [Agregar y eliminar observadores, cerrar y volver a abrir tickets](https://experienceleague.adobe.com/es/docs/commerce-learn/tutorials/help-and-support/add-remove-watchers-close-reopen-support-ticket).

### Vuelva a abrir el caso {#reopen-case}

>[!NOTE]
>
>**Solo puede reabrir un caso dentro de los 14 días posteriores a su cierre.** Si ya han pasado 14 días desde el cierre del caso, pero aun así desea solicitar ayuda en relación con un problema, debe abrir un nuevo caso.<br>Para obtener más información sobre cómo cerrar y reabrir casos, vea el vídeo [Agregar y quitar observadores, cerrar y reabrir tickets](https://experienceleague.adobe.com/es/docs/commerce-learn/tutorials/help-and-support/add-remove-watchers-close-reopen-support-ticket).

>[!NOTE]
>
>No puedes reabrir un caso respondiendo a una notificación por correo electrónico desde un ticket cerrado. Para reabrir el caso, asegúrate de que el propietario de la cuenta te haya dado [acceso compartido](https://experienceleague.adobe.com/es/docs/experience-cloud-kcs/kbarticles/ka-26164).

### Enviar ticket mediante la consola de Cloud {#cloud-console}

Para enviar un nuevo ticket de asistencia técnica mediante Cloud Console, siga estos pasos:

1. Inicie sesión en [Cloud Console](https://console.adobecommerce.com).
1. Seleccione **[!UICONTROL Support]** en el menú de usuario.
1. Se carga la página **[!UICONTROL My Tickets]**.
1. Haga clic en **[!UICONTROL Submit a ticket]** en la esquina superior derecha.
1. Rellene [los campos](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/faq/support-ticket-contact-reason-descriptions).
1. Haga clic en **[!UICONTROL Submit]**.

### Línea directa de Adobe Commerce P1 {#P1-hotline}

El artículo de la [línea directa P1 de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/adobe-commerce-p1-notification-hotline.html?lang=es) proporciona los números de la línea directa P1 para Adobe Commerce cuando se busca ayuda durante un incidente P1 y explica qué información se debe proporcionar.

### Modelo operativo de responsabilidad compartida de Adobe Commerce {#shared-responsibility-operational-model}

Consulte el artículo sobre [Modelo operativo de responsabilidad compartida de Adobe Commerce](https://experienceleague.adobe.com/es/docs/commerce-operations/security-and-compliance/shared-responsibility#operational-responsibilities-summary),
que tiene como objetivo aclarar las responsabilidades operativas de nuestra oferta de infraestructura Pro únicamente.

### Abra un ticket de seguimiento {#follow-up}

La apertura de un ticket de seguimiento garantizará que el problema original esté vinculado al ticket de seguimiento para garantizar la continuidad.

Para abrir un ticket de seguimiento, haga clic en el vínculo &quot;*crear un ticket de seguimiento*&quot; en la parte inferior del ticket en el que desea crear un ticket de seguimiento.

## ACCESO COMPARTIDO: CONCEDA PRIVILEGIOS PARA QUE OTROS USUARIOS ACCEDAN A SU CUENTA {#shared-access}

Puede conceder acceso limitado a su cuenta a otros titulares de cuentas de Adobe Commerce. En particular, al usar la funcionalidad **acceso compartido**, puede otorgar privilegios a empleados y proveedores de servicios de confianza para que usen su cuenta del Centro de ayuda y así poder trabajar con sus tickets de soporte técnico.

Puede proporcionar y administrar el acceso compartido mediante la página de cuenta de Adobe Commerce en [https://account.magento.com](https://account.magento.com/).

### Quién puede proporcionar acceso compartido {#who-can-provide-shared-access}

Solo el propietario de la cuenta (titular de la cuenta principal) con los privilegios correspondientes puede proporcionar acceso compartido a otros usuarios.

La gestión de los usuarios y su acceso es responsabilidad del cliente, especialmente en la perspectiva del acceso compartido. Por lo tanto, el equipo de asistencia de Adobe Commerce no puede proporcionar acceso compartido a una cuenta de Adobe Commerce en nombre de un cliente. Se recomienda a los clientes que agreguen usuarios con acceso compartido mediante la [página de cuenta de Adobe Commerce](https://account.magento.com/).

Los usuarios a los que se ha proporcionado acceso compartido no pueden transferir ni conceder dicho acceso a otros usuarios.

### Proporcionar acceso compartido {#provide-shared-access}

Consulte la sección [Compartir una cuenta de Commerce](https://experienceleague.adobe.com/es/docs/commerce-admin/start/commerce-account/commerce-account-share) de la Guía de introducción de Adobe Commerce para ver los pasos detallados sobre cómo configurar una cuenta compartida.

>[!NOTE]
>
>El usuario debe tener una cuenta existente para que se le pueda otorgar acceso compartido. Consulta [Crear una cuenta de Commerce](https://experienceleague.adobe.com/es/docs/commerce-admin/start/commerce-account/commerce-account-create#create-a-commerce-account) para obtener más detalles.

Después de proporcionar acceso compartido a un nuevo usuario, la información relacionada estará disponible en **Acceso compartido** > **Administrar permisos** de la página de la cuenta de Adobe Commerce.

>[!NOTE]
>
>El acceso compartido no concede automáticamente acceso a la consola de Commerce Cloud. Debe [agregar al usuario por separado al proyecto en la nube](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/project/user-access#add-a-user-to-the-project).

![permisos de administración compartida de cuentas de magento](assets/magento_account_shared_manage_permissions.png)

### Revocar (eliminar) el acceso compartido {#revoke-shared-access}

1. Inicie sesión en su cuenta de Adobe Commerce en [https://account.magento.com](https://account.magento.com/).
1. En el panel de la izquierda, en Acceso compartido, elija **Administrar permisos.**
1. Busque el usuario desde el que desea revocar el acceso compartido y haga clic en ![quitar icono](assets/remove_icon.png){width="25"} en la fila del usuario (columna **Acciones**).
1. Haga clic en **Eliminar usuario** para revocar el acceso o en X en la esquina superior para cancelar la revocación.

   ![revocar_acceso_compartido](assets/revoke_shared_access.png){width="800"}

   También puede revocar el acceso compartido mediante el menú **Editar**:

1. Inicie sesión en su cuenta de Adobe Commerce en [https://account.magento.com](https://account.magento.com/).
1. En el panel de la izquierda, en Acceso compartido, elija **Administrar permisos.**
1. Busque el usuario desde el que desea revocar el acceso compartido y haga clic en **Editar** en la fila del usuario (columna **Acciones**).
1. Haga clic en **Eliminar este usuario** en la parte inferior de la página.
1. En el elemento emergente de confirmación, haga clic en **Eliminar usuario** para revocar el acceso o en X en la esquina superior para cancelar la revocación.

### ¿Cómo eliminar a los usuarios a los que se les concedió acceso compartido a través de un proyecto de Cloud? {#remove-cloud-shared-access-users}

<u>Productos y versiones afectados</u>

* Adobe Commerce Cloud (todas las versiones)

<u>Causa</u>

Si tiene o ha tenido un proyecto de Adobe Commerce Cloud y ha agregado un usuario al proyecto, es posible que se le haya concedido automáticamente acceso compartido en el ID de IMAGEN del propietario del proyecto. Normalmente, esto se indica en la columna **[!UICONTROL Share Name]**, que muestra *Acceso compartido en la nube desde MAG[XYZ]*.

>[!NOTE]
>
>Si falta el vínculo de DELETE, significa que el acceso compartido se concedió automáticamente a través de Commerce Cloud.

<u>Solución</u>

No se puede eliminar la lista de usuarios de acceso compartido con el nombre compartido de *Acceso compartido de nube de MAG[XYZ]* si el acceso compartido no se agregó o asignó [en esta página](https://account.magento.com/grantor/manage/). Se conservan con fines informativos o de auditoría.

Sin embargo, una vez que haya revocado los permisos a esos usuarios de acceso compartido, ya no tendrán ese acceso.

1. Inicie sesión en su cuenta de Adobe Commerce en [https://account.magento.com](https://account.magento.com/).
1. En el panel de la izquierda, debajo de *[!UICONTROL Shared Access]*, elija **[!UICONTROL Manage Permissions]**.
1. Busque el usuario desde el que desea revocar el acceso compartido y haga clic en **[!UICONTROL Edit]** en la fila del usuario (columna *[!UICONTROL Actions]*).
1. Desmarque todos los recursos bajo *[!UICONTROL Grant Account Permissions]*.

![grant-account-permissions-image](assets/help-center-user-guide-grant-account-permissions-image.png){width="800"}

Para obtener más información, consulte la documentación de [Administrar el acceso de los usuarios](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=es#manage-users-from-the-project-web-interface) en nuestra Guía de infraestructura en la nube de Commerce.

### Acceso a una cuenta compartida (cuentas de conmutador) {#switch-accounts}

Para utilizar el acceso compartido proporcionado, siga estos pasos:

1. Inicie sesión en su cuenta de Adobe Commerce en [https://account.magento.com](https://account.magento.com/).
1. Haga clic en el menú **Cambiar cuentas** y seleccione una cuenta.

   ![conmutador-compartido-cuenta-magento](assets/magento_account_shared_switch.png){width="800"}

Para saber qué cuenta está usando actualmente (su propia cuenta nativa o acceso compartido), vea el menú **Cambiar cuentas**: muestra la cuenta activa.

### Solución de problemas de acceso compartido {#troubleshooting-shared-access}

Consulte el [artículo de solución de problemas con acceso compartido](/help/troubleshooting/miscellaneous/shared-access-troubleshooting.md) en nuestra base de conocimiento de asistencia.



