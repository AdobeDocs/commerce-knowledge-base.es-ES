---
title: Base de conocimiento de asistencia de Adobe Commerce
description: Todo lo que necesita saber para solucionar los problemas de su tienda Commerce y mantenerla.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 52d07e5a5bb7be492f6799d0e5ad9fd49c3a61ae
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 0%

---

# Base de conocimiento de asistencia de Adobe Commerce

>[!NOTE]
>
>La Guía de la base de conocimiento de asistencia de Adobe Commerce se reestructurará próximamente y su contenido se trasladará a otras ubicaciones de Adobe Experience League. Mientras tanto, seguiremos manteniendo y actualizando el contenido de esta guía.

![Página principal de Knowledge Base](../help/assets/knowledge-base-home-page-cover.jpg){width="100%"}

La información de esta base de conocimiento se ha diseñado como complemento de [Adobe Commerce Developer Documentation](https://developer.adobe.com/commerce/docs), [Adobe Commerce Merchant Guide](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html) y otras publicaciones de Adobe Commerce. Abarca la resolución de problemas y las prácticas recomendadas, contiene anuncios, responde a preguntas frecuentes y destaca escenarios específicos que no se han mencionado (por algún motivo) en la documentación oficial.

## ¿Qué hay en esta base de conocimiento?

| CATEGORÍA | DESCRIPCIÓN |
| --- | --- |
| [Herramientas de soporte](/help/support-tools/overview.md) | Mejore su experiencia de tienda de comercio electrónico con las diferentes herramientas de asistencia que proporciona Adobe Commerce. Proporcionamos prácticas recomendadas personalizadas, herramientas de diagnóstico y monitorización, y la información más relevante sobre su sitio. |
| [Anuncios](/help/announcements/overview.md) | Obtenga actualizaciones importantes de los equipos de Adobe Commerce. |
| [Solución de problemas](/help/troubleshooting/overview.md) | Obtenga soluciones de autoservicio y parches del equipo de asistencia de Adobe Commerce. |
| [Guía del usuario del Centro de ayuda](/help/help-center-guide/help-center/magento-help-center-user-guide.md) | Obtenga información sobre cómo administrar los vales de soporte, conceder acceso compartido y examinar la Base de conocimiento de forma eficaz. |
| [Procedimientos](/help/how-to/overview.md) | Obtenga instrucciones paso a paso claras del equipo de asistencia de Adobe Commerce. |
| [PREGUNTAS MÁS FRECUENTES](/help/faq/overview.md) | Encuentre las preguntas más frecuentes acerca de las políticas de Adobe Commerce, las estrategias y los detalles específicos acerca de las funciones de Adobe Commerce. |

## Novedades de la versión

<table style="width:100%">
  <tr>
    <th style="width:70%">Descripción</th>
    <th style="width:15%">Tipo</th>
    <th style="width:15%">Fecha</th>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25234">Transferencia de licencias debido a la reestructuración:</a> Este artículo le ayudará a realizar la transición de la propiedad de su cuenta de Adobe Commerce con facilidad, incluidos todos los pasos esenciales necesarios para mantener sus servicios en funcionamiento sin problemas.
    </td>
    <td>Nuevo artículo </td>
    <td>14 de noviembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25289">Actualizaciones de seguridad disponibles para Adobe Commerce (APSB24-90):</a> El 12 de noviembre de 2024, Adobe lanzó una actualización de seguridad para Adobe Commerce (en la nube y locales) y funciones de Magento Open Source con tecnología de Commerce Services e implementadas como SaaS (Software as a Service). Esta actualización resuelve una vulnerabilidad <a href="https://helpx.adobe.com/security/severity-ratings.html">critical</a>. 
    </td>
    <td>Nuevo artículo </td>
    <td>14 de noviembre de 2024</td>
  </tr>

<tr>
    <td>
    El propietario de la cuenta de <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25231">MageID no puede iniciar sesión y enviar una solicitud de asistencia:</a> Este artículo aborda el problema de Adobe Commerce en el cual no puede iniciar sesión en su cuenta (MageID) en account.magento.com para enviar una solicitud de asistencia.
    </td>
    <td>Nuevo artículo </td>
    <td>14 de noviembre de 2024</td>
  </tr>

<tr>
    <td>
    La extensión de Braintree <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25135">OOTB para Adobe Commerce no es compatible con los campos Visa 3DS más recientes:</a> En este artículo se explica cómo cumplir con las nuevas regulaciones de Visa, ya que la extensión de Braintree predeterminada de Adobe Commerce no es compatible con los campos Visa 3DS más recientes.
    </td>
    <td>Nuevo artículo </td>
    <td>14 de noviembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-61528-retrieving-roles-using-graphql-returns-no-results">ACSD-61528: la recuperación de roles mediante GraphQL no devuelve resultados:</a> El parche ACSD-61528 corrige el problema en el que la recuperación de roles del administrador de la empresa mediante GraphQL siempre devuelve un resultado nulo. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.53.
    </td>
    <td>Nuevo artículo </td>
    <td>14 de noviembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-48318-environment-emulation-nesting-error-in-system-log">ACSD-48318: error de anidación de emulación de entorno en system.log:</a> El parche ACSD-48318 corrige el problema en el que aparece un mensaje de error <em>main.ERROR:No se permite el anidamiento de emulación de entorno</em> en <code>system.log</code> cada vez que se envía un correo electrónico de factura. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.53.
    </td>
    <td>Nuevo artículo </td>
    <td>14 de noviembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59366-delete-teams-with-deactivated-users-not-visible-in-the-team-list">ACSD-59366: Eliminar equipos con usuarios desactivados que no están visibles en la lista de equipos:</a> La revisión ACSD-59366 corrige el problema en el que se produce un error al intentar eliminar un equipo que contiene usuarios desactivados que no están visibles en la lista de equipos. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.52.
    </td>
    <td>Nuevo artículo </td>
    <td>14 de noviembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60234-paypal-shows-an-incorrect-amount-when-discount-is-applied">ACSD-60234: PayPal muestra una cantidad incorrecta cuando se aplica el descuento:</a> El parche ACSD-60234 corrige el problema en el que [!DNL PayPal] muestra una cantidad incorrecta cuando el descuento se aplica a través del método de pago. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.51.
    </td>
    <td>Nuevo artículo </td>
    <td>14 de noviembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60673-cart-price-rule-fix-for-multiple-payment-methods-at-checkout">ACSD-60673: problema con la regla de precio del carro de compras corregido para varios métodos de pago al finalizar la compra:</a> El parche ACSD-60673 corrige el problema en el que los descuentos de un [!UICONTROL Cart Price Rule] que utilizan una condición de método de pago no siempre se enumeran en los totales. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.52.
    </td>
    <td>Nuevo artículo </td>
    <td>14 de noviembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-60584-access-token-created-for-one-website-is-allowed-to-access-information-on-other-websites">ACSD-60584: el token de acceso creado para un sitio web puede tener acceso a información de otros sitios web:</a> El parche ACSD-60584 corrige el problema en el que el token de acceso creado para el usuario en un sitio web puede tener acceso o cambiar la información de los clientes en otros sitios web. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.53.
    </td>
    <td>Nuevo artículo </td>
    <td>14 de noviembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60788-fixes-issue-where-custom-scripts-for-google-tag-manager-are-not-executed-due-to-content-security-policy-errors">ACSD-60788: los scripts personalizados para Google Tag Manager no se ejecutan debido a errores de la directiva de seguridad de contenido:</a> El parche ACSD-60788 corrige el problema en el que los scripts personalizados para [!DNL Google Tag Manager] no se ejecutan debido a errores de la directiva de seguridad de contenido. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.52.
    </td>
    <td>Nuevo artículo </td>
    <td>14 de noviembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-61366-setup-command-fails-with-error">ACSD-61366: el comando <code>bin/magento setup:static-content:deploy --jobs 4</code> encuentra varios errores de trabajo con un error:</a> El parche ACSD-61366 corrige el problema en el que el comando <code>bin/magento setup:static-content:deploy --jobs 4</code> encuentra varios errores de trabajo con el error <em>El puerto debe configurarse dentro del parámetro de host</em>, a pesar de especificar el puerto para la conexión DB. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.52.
    </td>
    <td>Nuevo artículo </td>
    <td>14 de noviembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60816-newrelic-browser-monitoring-scripts-injected-by-apm-agent-are-not-compliant-with-csp">ACSD-60816: los scripts de supervisión del explorador New Relic insertados por el agente de APM no son compatibles con el CSP:</a> El parche ACSD-60816 corrige el problema en el que los scripts de supervisión del explorador [!DNL New Relic] insertados por el agente de APM no son compatibles con la Política de seguridad de contenido (CSP). Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.51.
    </td>
    <td>Nuevo artículo </td>
    <td>14 de noviembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59952-error-on-deleting-shared-catalog-with-same-group-id-as-another-shared-catalog">ACSD-59952: error al eliminar el catálogo compartido con el mismo identificador de grupo que otro catálogo compartido:</a> El parche de ACSD-59952 corrige el error producido al eliminar los catálogos compartidos con el mismo <code>customer_group_id</code> que otro catálogo compartido. Además, evita que los usuarios creen este tipo de catálogos compartidos. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.52.
    </td>
    <td>Nuevo artículo </td>
    <td>14 de noviembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-59786-graphql-returns-an-error-when-fetching-a-quote-id-for-an-expired-quote">ACSD-59786: GraphQL devuelve un error al recuperar un <code>quote_id</code> para una oferta caducada:</a> La revisión ACSD-59786 corrige el problema en el que una consulta GraphQL devuelve un error al recuperar un <code>quote_id</code> para una oferta caducada. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.51.
    </td>
    <td>Nuevo artículo </td>
    <td>14 de noviembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-59967-javascript-error-prevents-google-maps-from-rendering-correctly">ACSD-59967: el error de JavaScript impide que Google Maps se represente correctamente:</a> El parche ACSD-59967 corrige el problema en el que el error de JavaScript impide que [!DNL Google Maps] se represente correctamente. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.51.
    </td>
    <td>Nuevo artículo </td>
    <td>14 de noviembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-59930-improves-performance-of-company-flows">ACSD-59930: mejora el rendimiento de los flujos de la compañía:</a> El parche ACSD-59930 corrige el problema en el que se muestra un error <em>Timeout</em> en el panel de administración al crear, guardar o eliminar una compañía con un administrador que tenga más de 1000 direcciones en la libreta de direcciones. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.53.
    </td>
    <td>Nuevo artículo </td>
    <td>14 de noviembre de 2024</td>
  </tr>
</table>
