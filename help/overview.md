---
title: Base de conocimiento de asistencia de Adobe Commerce
description: Todo lo que necesita saber para solucionar los problemas de su tienda Commerce y mantenerla.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 6d22ea4725249df1528625672be405464b1411e8
workflow-type: tm+mt
source-wordcount: '920'
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
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25301">Resolver [!DNL New Relic] problemas del agente con la actualización de PHP 8.2 a 8.3 en Adobe Commerce:</a> Al actualizar PHP de la versión 8.2 a la 8.3, es posible que observe que el agente [!DNL New Relic] deja de funcionar en su entorno de Adobe Commerce. Este problema se ha observado en entornos de ensayo y producción. En este artículo, encontrará los pasos para solucionar y resolver este problema.
    </td>
    <td>Nuevo artículo </td>
    <td>5 de diciembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25321">[!DNL Security Scan Tool] devuelve "Actualizaciones de seguridad de APSByy-xx disponibles" incluso si el parche ya se ha aplicado:</a> [!DNL Security Scan Tool] informa de que hay actualizaciones de seguridad de APSByy-xx disponibles para Adobe Commerce y Magento Open Source aunque ya haya aplicado el parche. Puede ignorar esta notificación.
    </td>
    <td>Nuevo artículo </td>
    <td>5 de diciembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61845-error-occurs-for-requests-with-text-html-accept-header">ACSD-61845: Error en solicitudes con encabezado de aceptación de texto/html:</a> El parche ACSD-61845 corrige el problema en el que una solicitud HTTP con un encabezado de aceptación de texto/html provoca un error 500 debido a discrepancias de tipo de medios en la administración de respuestas. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.54.
    </td>
    <td>Nuevo artículo </td>
    <td>5 de diciembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61200-fixes-discount-tax-compensation-in-sales-total-calculations">ACSD-61200: compensación de impuestos de descuento incorrecta en los cálculos de totales de ventas:</a> El parche ACSD-61200 corrige el problema en el que el importe de compensación de impuestos de descuento y el importe de compensación de impuestos de descuento de envío no aparecen en los cálculos Importe total e Importe total real, lo que da como resultado discrepancias entre los datos del pedido de ventas y los datos del informe de cupones. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.54.
    </td>
    <td>Nuevo artículo </td>
    <td>5 de diciembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61199-cms-page-hierarchy-tab-doesnt-display-proper-tree-structure">ACSD-61199: la ficha [!UICONTROL Hierarchy] de la página de CMS no muestra la estructura de árbol adecuada:</a> El parche ACSD-61199 corrige el problema en el que la ficha [!UICONTROL Hierarchy] de la página de CMS no muestra una estructura de árbol adecuada al editar una página de CMS con una jerarquía existente. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.54.
    </td>
    <td>Nuevo artículo </td>
    <td>5 de diciembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-60804-editing-customer-linked-to-deleted-company-causes-error">ACSD-60804: al editar un cliente asociado con una compañía eliminada, se produce un error:</a> El parche de ACSD-60804 corrige el problema en el que al editar un cliente asociado con una compañía eliminada, se produce un error <em>Llamada a una función de miembro getSuperUserId() en null</em>. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.53.
    </td>
    <td>Nuevo artículo </td>
    <td>5 de diciembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61522-email-in-name-fields-sends-invalid-order-confirmations">ACSD-61522: las direcciones de correo electrónico de los campos [!UICONTROL First] y [!UICONTROL Last Name] envían confirmaciones de pedido no válidas:</a> El parche de ACSD-61522 corrige el problema en el que es posible introducir direcciones de correo electrónico en los campos [!UICONTROL First Name] y [!UICONTROL Last Name] de un cliente invitado, lo que provoca que se envíen correos electrónicos de confirmación de pedido no válidos. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.54.
    </td>
    <td>Nuevo artículo </td>
    <td>5 de diciembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-62485-async-operations-all-consumer-stops-working-when-company-is-created">ACSD-62485: <code>async.operations.all</code> el consumidor deja de funcionar cuando se crea la compañía:</a> El parche ACSD-62485 corrige el problema en el que el consumidor <code>async.operations.all</code> deja de funcionar cuando se crea una compañía B2B. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.54.
    </td>
    <td>Nuevo artículo </td>
    <td>5 de diciembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60684-graphql-product-sorting-by-multiple-fields-does-not-work-as-expected">ACSD-60684: la ordenación de productos de GraphQL por varios campos no funciona de la forma esperada:</a> El parche de ACSD-60684 corrige el problema en el que la ordenación de productos de GraphQL por varios campos no funciona cuando se pasa la ordenación en variables. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.52.
    </td>
    <td>Nuevo artículo </td>
    <td>5 de diciembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-61553-cart-price-rule-discounts-are-incorrectly-calculated-when-multiple-discounts-with-different-priorities-are-applied">ACSD-61553: [!UICONTROL Cart Price Rule] se calcula incorrectamente cuando se aplican varios descuentos con prioridades diferentes:</a> El parche ACSD-61553 corrige el problema en el que [!UICONTROL Cart Price Rule] se calcula incorrectamente cuando se aplican varios descuentos con prioridades diferentes. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.53.
    </td>
    <td>Nuevo artículo </td>
    <td>5 de diciembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-58383-duplicate-credit-memos-from-simultaneous-refund-requests-via-rest-api">Parche de Adobe Commerce ACSD-58383: duplicar notas de crédito de solicitudes de reembolso simultáneas a través de la API REST:</a> El parche de ACSD-58383 corrige el problema en el que emitir un reembolso a través de la API REST con dos solicitudes idénticas que se ejecutan simultáneamente, resulta en notas de crédito duplicadas. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.55.
    </td>
    <td>Nuevo artículo </td>
    <td>5 de diciembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-58471-dynamic-content-fails-load-product-detail-page">ACSD-58471: el contenido dinámico no se puede cargar en la página de detalles del producto, cuando se programaron las reglas de precios del catálogo asociadas:</a> El parche ACSD-58471 resuelve el problema de que el contenido dinámico no se puede cargar en la página de detalles del producto, cuando se programaron las reglas de precios del catálogo asociadas. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.55.
    </td>
    <td>Nuevo artículo </td>
    <td>5 de diciembre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-58735-restricted-admin-cant-view-abandoned-shopping-carts">ACSD-58735: el administrador restringido no puede ver los carros de compras abandonados en la cuenta de cliente del sitio web asociado:</a> El parche ACSD-58735 corrige el problema en el que un usuario administrador con un rol restringido no puede ver los carros de compras de los clientes abandonados desde la pestaña <strong>[!UICONTROL Commerce Admin]</strong> &gt; <strong>[!UICONTROL Reports]</strong> &gt; <strong>[!UICONTROL Abandoned Carts]</strong> &gt; <strong>[!UICONTROL Select Cart]</strong> &gt; <strong>[!UICONTROL Shopping Cart]</strong>. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.55.
    </td>
    <td>Nuevo artículo </td>
    <td>5 de diciembre de 2024</td>
  </tr>
</table>
