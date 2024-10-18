---
title: Base de conocimiento de asistencia de Adobe Commerce
description: Todo lo que necesita saber para solucionar los problemas de su tienda Commerce y mantenerla.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 607b835da518536196654734f62d78d095099476
workflow-type: tm+mt
source-wordcount: '1615'
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
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25075">La herramienta de exploración de seguridad devuelve el mensaje "No se puede determinar si el servidor usa 2FA":</a> Para resolver el error, compruebe si el módulo <code>Magento_TwoFactorAuth</code> se ha deshabilitado. Para pasar la comprobación, en general, debe estar activada.
    </td>
    <td>Nuevo artículo </td>
    <td>17 de octubre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60632-address-saved-on-every-order-attempt">ACSD-60632: dirección guardada con cada intento de pedido:</a> El parche de ACSD-60632 corrige el problema en el que se guarda una nueva dirección con cada intento de colocación de pedido, independientemente de si el pedido se ha creado correctamente o no. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.51.
    </td>
    <td>Nuevo artículo </td>
    <td>17 de octubre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60326-graphql-query-error-customer-return-status">ACSD-60326: la consulta de GraphQL sobre el estado Devuelve del cliente da un error:</a> El parche de ACSD-60326 corrige el problema en el que se produce un error en la consulta de GraphQL para el estado Devuelve del cliente. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.51.
    </td>
    <td>Nuevo artículo </td>
    <td>17 de octubre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59925-sorting-items-in-media-gallery">ACSD-59925: ordenar elementos de la Galería multimedia por posición en GraphQL:</a> El parche de ACSD-59925 corrige el problema en el que los elementos de la Galería multimedia no se ordenan por posición, lo que da lugar a un orden de visualización incorrecto. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.52.
    </td>
    <td>Nuevo artículo </td>
    <td>17 de octubre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-61322-products-not-assigned-to-shared-catalogue">ACSD-61322: los productos no asignados al catálogo compartido se incluyen en el mapa del sitio XML:</a> El parche ACSD-61322 corrige el problema en el que los productos o categorías no asignados al catálogo compartido para el grupo Predeterminado (General) siguen incluidos en el mapa del sitio XML. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.52.
    </td>
    <td>Nuevo artículo </td>
    <td>17 de octubre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60590-optimized-bestseller-report-generation">ACSD-60590: mejorando el rendimiento de generación de informes diarios agregados de Bestsellers:</a> El parche de ACSD-60590 corrige el problema en el que el informe diario agregados de Bestsellers tarda una cantidad de tiempo considerable en generarse para un gran volumen de pedidos realizados. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.52.
    </td>
    <td>Nuevo artículo </td>
    <td>17 de octubre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59865-cart-price-rule-fix-for-insufficient-quantity-issue">ACSD-59865: la regla de precio del carro de compras no puede cancelar las reglas anteriores debido a una cantidad de producto insuficiente:</a> El parche ACSD-59865 corrige el problema en el que el valor de <em>Paso de cantidad de descuento</em> en <em>Descuento de cantidad fija</em>, <em>Porcentaje de descuento en el precio del producto</em> y <em>Comprar X obtener Y</em> Reglas de precio del carro de compras ya no cancela la acción de las reglas anteriores. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.52.
    </td>
    <td>Nuevo artículo </td>
    <td>17 de octubre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/error-when-filtering-orders-in-admin">Error al filtrar pedidos en el administrador:</a> Este artículo proporciona un parche para el problema de Adobe Commerce donde se produce un error al intentar filtrar pedidos en el administrador por fecha, mostrando el mensaje: <em>Infracción de restricción de integridad: 1052 Columna 'created_at' donde la cláusula es ambigua</em>.
    </td>
    <td>Nuevo artículo </td>
    <td>17 de octubre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25030">Adobe Commerce: problemas de JavaScript en línea en la página de cierre de compra en el modo restringido de la directiva de seguridad de contenido (CSP):</a> Este artículo proporciona explicaciones detalladas y soluciones para los problemas encontrados con el JavaScript personalizado agregado mediante el administrador de Adobe Commerce y el administrador de etiquetas de Google en Adobe Commerce 2.4.7 durante el cierre de compra cuando el <strong>modo restringido de CSP</strong> está habilitado.
    </td>
    <td>Nuevo artículo </td>
    <td>17 de octubre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-61195-empty-cart-on-final-graphql-page">ACSD-61195: la solicitud de GraphQL del carro de compras no puede devolver elementos en la página final:</a> El parche de ACSD-61195 corrige el problema en el que no se devuelven elementos del carro de compras en la última página de la solicitud de GraphQL del carro de compras. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.51.
    </td>
    <td>Nuevo artículo </td>
    <td>17 de octubre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-50/acsd-59514-forms-in-admin-with-page-builder-throw-error-in-browser-console">ACSD-59514: Forms en el administrador con el generador de páginas produjo un error en la consola del explorador:</a> El parche de ACSD-59514 corrige el problema en el que los formularios en el administrador con el generador de páginas generaron el error <em>El generador de páginas estaba procesando durante 5 segundos sin liberar bloqueos</em> en la consola del explorador después de enviar el formulario, y los cambios no se pueden guardar. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.50.
    </td>
    <td>Nuevo artículo </td>
    <td>17 de octubre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60538-if-product-is-disabled-attributes-dont-show">ACSD-60538: los atributos no se muestran correctamente si el producto está deshabilitado en <em>Todas las vistas de la tienda</em>:</a> La revisión ACSD-60538 corrige el problema en el que si un producto está deshabilitado en <em>Todas las vistas de la tienda</em> y habilitado solo en ámbitos específicos de vista de la tienda, los atributos del producto no se muestran correctamente en la respuesta de GraphQL, lo que provoca que el producto no se muestre correctamente. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.51.
    </td>
    <td>Nuevo artículo </td>
    <td>17 de octubre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-50/acsd-58352-return-attribute-labels-for-the-default-store-are-returned-via-graphql-api">ACSD-58352: las etiquetas de atributos de devolución de la tienda predeterminada se devuelven mediante la API de GraphQL:</a> La revisión ACSD-58352 corrige el problema en el que las etiquetas de atributos de devolución de la tienda predeterminada se devuelven mediante la API de GraphQL cuando se especifica una vista de tienda no predeterminada en el encabezado de la solicitud. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.50.
    </td>
    <td>Nuevo artículo </td>
    <td>17 de octubre de 2024</td>
  </tr>

<tr>
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-24983">Falta el menú desplegable <em>Cuentas de conmutador</em> en tu cuenta:</a> Este artículo proporciona una solución al problema de Adobe Commerce donde el menú desplegable <em>Cuentas de conmutador</em> no está en tu cuenta y has perdido el acceso para enviar tickets en nombre del comerciante.
    </td>
    <td>Nuevo artículo</td>
    <td>17 de octubre de 2024</td>
  </tr>

<tr>  
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-56979-product-images-removed-after-staging-update-deleted">ACSD-56979: imágenes de producto eliminadas después de eliminar la actualización de ensayo:</a> El parche ACSD-56979 corrige el problema en el que las imágenes de producto se eliminan después de eliminar una actualización de ensayo. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.49.  
    </td>
    <td>Nuevo artículo</td>
    <td>17 de octubre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-48210-store-view-specific-scope-attribute-overrides-global-values">ACSD-48210: los atributos de ámbito específicos de vista de tienda anulan los valores globales:</a> El parche de ACSD-48210 corrige el problema en el que al actualizar un atributo de <em>Ámbito de sitio web</em> dentro de una vista de almacén específica, se anulan los valores de atributo en el ámbito global. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.50. 
    </td>
    <td>Nuevo artículo </td>
    <td>17 de octubre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-59280-fix-for-reflection-union-type-error">ACSD-59280: error ReflectionUnionType::getName() en instalaciones 2.4.4-pX:</a> El parche ACSD-59280 corrige el problema en el que se produce el error de llamada al método indefinido <code>ReflectionUnionType::getName()</code> durante la instalación de las versiones 2.4.4-pX. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.50. 
    </td>
    <td>Nuevo artículo </td>
    <td>17 de octubre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-54887-customer-shopping-cart-gets-cleared-after-session-expiry">ACSD-54887: el carro de compras del cliente se borra después de que la sesión del cliente haya caducado:</a> El parche ACSD-54887 corrige el problema en el que el carro de compras del cliente se borra después de que la sesión del cliente haya caducado con el <em>carro de compras persistente</em> habilitado. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.50. 
    </td>
    <td>Nuevo artículo </td>
    <td>17 de octubre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-60303-admin-order-placement-fix">ACSD-60303: problema de colocación de orden de administración resuelto con la minificación de HTML habilitada:</a> El parche de ACSD-60303 corrige el problema en el que no se puede realizar un pedido de administrador si la minificación de HTML está habilitada. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.50. 
    </td>
    <td>Nuevo artículo </td>
    <td>17 de octubre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-57045-url-rewrites-cause-infinite-page-looping-after-website-root-unchecked-hierarchy">ACSD-57045: las reescrituras de URL provocan bucles de página infinitos después de que <em>Raíz del sitio web</em> no esté marcada en la jerarquía:</a> El parche ACSD-57045 corrige el problema en el que las reescrituras de URL provocan bucles de página infinitos después de que <em>Raíz del sitio web</em> esté desmarcada en la jerarquía. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.49.
    </td>
    <td>Nuevo artículo </td>
    <td>17 de octubre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/ascd-58446-deleting-a-team-with-child-users-or-teams-via-graphql-gives-an-uninformative-error-message">ACSD-58446: al eliminar un equipo con usuarios o equipos secundarios a través de GraphQL, se muestra un mensaje de error no informativo:</a> El parche de ACSD-58446 corrige el problema de Adobe Commerce, donde al eliminar un equipo con usuarios o equipos secundarios a través de GraphQL, se devuelve un mensaje de error no informativo incoherente con la interfaz de usuario. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.49. 
    </td>
    <td>Nuevo artículo </td>
    <td>17 de octubre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-58375-wrong-youtube-api-key-configuration-causes-an-error-when-adding-a-youtube-video-at-the-store-view-level">ACSD-58735: La clave de API de YouTube configurada incorrectamente provoca un error al agregar vídeo en el nivel de vista de tienda:</a> La revisión ACSD-58735 corrige el problema en el que una configuración incorrecta de la clave de API de YouTube provoca un error al agregar un vídeo de YouTube en el nivel de vista de tienda. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.49. 
    </td>
    <td>Nuevo artículo </td>
    <td>17 de octubre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-57086-orders-placed-from-non-default-websites-with-terms-conditions-processed-incorrectly">ACSD-57086: los pedidos de sitios web no predeterminados con términos y condiciones habilitados se procesan incorrectamente:</a> El parche ACSD-57086 corrige el problema en el que los pedidos realizados desde sitios web no predeterminados con términos y condiciones habilitados no se procesan correctamente. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.49. 
    </td>
    <td>Nuevo artículo </td>
    <td>17 de octubre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58141-phpsessid-regenerates-on-post-requests-for-logged-in-customers-with-l2-redis-cache-enabled">ACSD-58141: PHPSESSID se regenera en solicitudes de POST para clientes que iniciaron sesión si está habilitada la memoria caché de L2 Redis:</a> El parche de ACSD-58141 corrige el problema en el que PHPSESSID se regenera en solicitudes de POST para un cliente que inició sesión si la memoria caché de L2 Redis está habilitada y el cliente se actualiza desde Administración. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.50. 
    </td>
    <td>Nuevo artículo </td>
    <td>17 de octubre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58790-fixes-pinch-to-zoom-functionality-on-the-product-detail-page-images-in-mobile-view-on-chrome">ACSD-58790: corrige la funcionalidad de pellizco para zoom en las imágenes de la página de detalles del producto en la vista móvil en Chrome:</a> El parche ACSD-58790 corrige el problema de Adobe Commerce en el que la imagen en la vista móvil en Chrome no hacía zoom en la imagen como se esperaba. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.50. 
    </td>
    <td>Nuevo artículo </td>
    <td>17 de octubre de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58442-fixes-issue-devices-768px-mobile-view-instead-desktop">ACSD-58442: corrige el problema en el que los dispositivos con una anchura de 768 píxeles se tratan como móviles, lo que provoca que el menú y el encabezado se carguen en la vista móvil en lugar de en el escritorio:</a> El parche ACSD-58442 corrige el problema de Adobe Commerce en el que los dispositivos con una anchura de 768 píxeles se tratan como móviles, lo que provoca que el menú y el encabezado se carguen en una vista móvil en lugar de en un escritorio. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.50.
    </td>
    <td>Nuevo artículo </td>
    <td>17 de octubre de 2024</td>
  </tr>
</table>
