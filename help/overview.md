---
title: Base de conocimiento de asistencia de Adobe Commerce
description: Todo lo que necesita saber para solucionar los problemas de su tienda Commerce y mantenerla.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 95509b717d41436b68ad94c3c28ac72e1887fdfc
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 1%

---

# Base de conocimiento de asistencia de Adobe Commerce

![Página principal de Knowledge Base](../help/assets/knowledge-base-home-page-cover.jpg){width="100%"}

La información de esta base de conocimiento está diseñada como complementaria de [Documentación para desarrolladores de Adobe Commerce](https://developer.adobe.com/commerce/docs), y [Guía de Adobe Commerce Merchant](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html)y otras publicaciones de Adobe Commerce. Abarca la resolución de problemas y las prácticas recomendadas, contiene anuncios, responde a preguntas frecuentes y destaca escenarios específicos que no se han mencionado (por algún motivo) en la documentación oficial.

## ¿Qué hay en la base de conocimientos?

| CATEGORÍA | DESCRIPCIÓN |
| --- | --- |
| [Herramientas de soporte](/help/support-tools/overview.md) | Mejore su experiencia de tienda de comercio electrónico con las diferentes herramientas de asistencia que proporciona Adobe Commerce. Proporcionamos prácticas recomendadas personalizadas, herramientas de diagnóstico y monitorización, y la información más relevante sobre su sitio. |
| [Anuncios](/help/announcements/overview.md) | Obtenga actualizaciones importantes de los equipos de Adobe Commerce. |
| [Solución de problemas](/help/troubleshooting/overview.md) | Obtenga soluciones de autoservicio y parches del equipo de asistencia de Adobe Commerce. |
| [Guía del usuario del Centro de ayuda](/help/help-center-guide/help-center/magento-help-center-user-guide.md) | Obtenga información sobre cómo administrar los vales de soporte, conceder acceso compartido y examinar la Base de conocimiento de forma eficaz. |
| [Procedimientos](/help/how-to/overview.md) | Obtenga instrucciones paso a paso claras del equipo de asistencia de Adobe Commerce. |
| [FAQ](/help/faq/overview.md) | Encuentre las preguntas más frecuentes acerca de las políticas de Adobe Commerce, las estrategias y los detalles específicos acerca de las funciones de Adobe Commerce. |

>[!NOTE]
>
>Para presentar un nuevo ticket, inicie sesión en [Centro de ayuda de Adobe Commerce](https://support.magento.com/) y siga los pasos detallados en [Enviar un ticket de asistencia](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket).
>
>Si no ve la opción de enviar un ticket, consulte la *[No se muestra el vínculo Enviar un ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#no-submit-link)* en nuestra sección [Guía del usuario del Centro de ayuda](/help/help-center-guide/help-center/magento-help-center-user-guide.md).

## Novedades de la versión

<table style="width:100%">
  <tr>
    <th style="width:70%">Descripción</th>
    <th style="width:15%">Tipo</th>
    <th style="width:15%">Fecha</th>
  </tr>

<tr>
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-update-the-cloud-account-profile">Actualización del perfil de la cuenta en la nube:</a> Este artículo proporciona pasos sobre cómo modificar el perfil en la cuenta de la nube.
    </td>
    <td>Nuevo artículo</td>
    <td>22 de abril de 2024</td>
  </tr>

<td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/payments/admin-create-order-page-in-csp-restricted-mode">Solucionar problemas de la página Crear pedido en el modo restringido CSP:</a> Este artículo proporciona explicaciones y correcciones para los problemas de Adobe Commerce 2.4.7 al crear un pedido en el lado del administrador cuando el modo restringido CSP es <em>Habilitado</em>.  
    </td>
    <td>Nuevo artículo</td>
    <td>22 de abril de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/payments/storefront-checkout-page-in-csp-restricted-mode">Solucionar problemas de la página de cierre de tienda en modo restringido CSP:</a> Este artículo proporciona explicaciones y correcciones para los problemas de Adobe Commerce 2.4.7 mientras ve la página de cierre de compra en modo restringido CSP, con la variable <em>"Se ha rechazado ejecutar un script en línea porque infringe la siguiente directiva de la política de seguridad de contenido: "script-src ..."</em> mensaje de error en el registro de la consola del explorador. 
    </td>
    <td>Nuevo artículo </td>
    <td>22 de abril de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-46/acsd-54656-invisible-recaptcha-fails-during-checkout-preventing-order-placement">ACSD-54656: reCAPTCHA invisible no funciona durante el cierre de compra, lo que impide la colocación de pedidos:</a> El parche ACSD-54656 soluciona el problema de que el reCAPTCHA invisible no funciona correctamente durante el cierre de compra, lo que impide realizar un pedido. Este parche está disponible cuando la variable <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.46 está instalado. 
    </td>
    <td>Nuevo artículo </td>
    <td>22 de abril de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-46/acsd-46767-category-page-caches-invalidate-when-the-stock-quantity-changes">ACSD-46767: Las cachés de la página Categoría se invalidan cuando cambia la cantidad de stock:</a> El parche ACSD-46767 corrige el problema en el que la página Categoría invalida la caché cuando cambia la cantidad de existencias, incluso si el producto aún está en existencias. Este parche está disponible cuando la variable <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.46 está instalado.  
    </td>
    <td>Nuevo artículo </td>
    <td>22 de abril de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-45/acsd-56415-performance-of-partial-price-indexing-is-slowed-down-due-to-a-delete-query">ACSD-56415: El rendimiento de la indexación de precios parciales se ralentiza debido a la consulta del DELETE:</a> El parche ACSD-56415 corrige el problema en el que el rendimiento de la indexación de precios parciales se ralentiza debido a una consulta del DELETE cuando la base de datos tiene un montón de índice de datos de precios parciales. Este parche está disponible cuando la variable <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.45 está instalado.  
    </td>
    <td>Nuevo artículo </td>
    <td>22 de abril de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-56858-role-permissions-display-issue-in-b2b-company-admin-panel">ACSD-56858: discrepancia en los permisos de funciones en el administrador de la empresa B2B:</a> El parche ACSD-56858 corrige el problema de que los permisos de funciones se muestran incorrectamente para un administrador de empresa restringido en el entorno B2B. Este parche está disponible cuando la variable <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47 está instalado. 
    </td>
    <td>Nuevo artículo </td>
    <td>22 de abril de 2024</td>
 </tr>
</table>

## Artículos populares

* [Cambio a OpenSearch para Adobe Commerce en la nube 2.4.4](/help/announcements/adobe-commerce-announcements/switching-to-opensearch-for-adobe-commerce-on-cloud-2-4-4.md)
* [Vulnerabilidad de Apache log4j2 en Adobe Commerce](/help/announcements/adobe-commerce-announcements/apache-log4j2-adobe-commerce.md)
* [Actualizaciones de seguridad disponibles para Adobe Commerce APSB22-12](/help/troubleshooting/known-issues-patches-attached/0-day-vulnerability-patch.md)
* [Identificar y medir las interrupciones de Adobe Commerce en la infraestructura en la nube](/help/how-to/general/how-to-identify-outages.md)
* [Vea el nivel de vCPU del entorno en su clúster en Adobe Commerce](/help/how-to/general/check-vcpu-using-observation-for-adobe-commerce.md)
* [Adobe Commerce en la infraestructura en la nube: cálculo de asignación de CPU](/help/how-to/general/magento-commerce-cloud-cpu-allocation-calculation.md)
* [Adobe Commerce en la infraestructura de la nube: Compruebe la configuración de CPU del host.](/help/how-to/general/magento-commerce-cloud-check-hosts-cpu-configuration.md)
