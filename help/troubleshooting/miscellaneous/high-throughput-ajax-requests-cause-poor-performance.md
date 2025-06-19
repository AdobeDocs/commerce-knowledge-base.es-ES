---
title: Las solicitudes de AJAX de alto rendimiento causan un rendimiento deficiente
description: Este artículo proporciona una solución para los problemas de rendimiento con Adobe Commerce local o Adobe Commerce en sitios de infraestructura en la nube debido a que algunas solicitudes de alto rendimiento causan una carga y un tráfico de servidor significativos.
exl-id: 68dfca8a-826c-4476-acaf-a139052b5dcc
feature: Cache
role: Developer
source-git-commit: b6e44e106dcc546949459a79c0f2e49b87e1d376
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# Las solicitudes de AJAX de alto rendimiento causan un rendimiento deficiente

Este artículo proporciona una solución para los problemas de rendimiento con Adobe Commerce local o Adobe Commerce en sitios de infraestructura en la nube debido a que algunas solicitudes de alto rendimiento causan una carga y un tráfico de servidor significativos.

## Productos y versiones afectados

* Adobe Commerce en cloud Infrastructure 2.2.x, 2.3.x
* Adobe Commerce local 2.2.x, 2.3.x

>[!NOTE]
>
>El problema se solucionó en la versión 2.3.4 de Adobe Commerce en la infraestructura en la nube y de Adobe Commerce en línea.

### Problema

El sitio experimenta un rendimiento lento debido a solicitudes de alto rendimiento, como solicitudes críticas de AJAX.

### Causa

Las solicitudes de AJAX de alto rendimiento incluyen las relacionadas con el contenido privado de los clientes.

### Solución

Hay tres soluciones:

* [Actualice a la versión 2.3.4](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version).
* Asegúrese de que las solicitudes sean más ligeras (almacene en caché las solicitudes o cambie al contenido privado de los clientes).
* Reduzca el número de solicitudes.

<u>Asegúrese de que las solicitudes sean más ligeras (solicitudes de caché o movimiento al contenido privado de los clientes)</u>

Si hay solicitudes de AJAX de terceros que se activan en cada página, intente almacenar en caché estas solicitudes o moverlas al contenido privado de los clientes. El comerciante puede hacerlo asegurándose de que se llama a las solicitudes de AJAX personalizadas mediante los métodos HTTP de GET. Hará que Fastly pueda almacenar en caché estas solicitudes. Si hay solicitudes de AJAX personalizadas que no deban almacenarse en caché, deben refactorizarse según la funcionalidad del contenido privado. Para ver los pasos, consulte [Contenido privado](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) en nuestra documentación para desarrolladores.

<u>Reducir el número de solicitudes</u>

* Deshabilite el carro de compras persistente, ya que puede aumentar el número de `customer/section/load` solicitudes. Siga los pasos de [Rutas de carro de compras persistentes](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/paths/config-reference-general) en nuestra documentación para desarrolladores para ver si el carro de compras persistente está habilitado.
* Si necesita volver a cargar o invalidar contenido en `sections.xml`, siga los pasos de [Contenido privado: invalide el contenido privado](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content) en nuestra documentación para desarrolladores. Asegúrese de que no está utilizando el método `customerData.reload()` directamente en las personalizaciones.
* Compruebe otras solicitudes de POST AJAX en la misma página. Abra la herramienta para desarrolladores de Google Chrome en el explorador Chrome de Google. Haz clic en la pestaña **Red** y luego en la pestaña **XHR**, y allí estará la lista de todas las solicitudes de AJAX de la página en particular. A continuación, haga clic en cada solicitud y, en el campo Método de solicitud debe estar las solicitudes de GET. Nota: Google Chrome se utiliza como ejemplo y también es posible hacerlo en otros exploradores.
* Compruebe la funcionalidad de Google Tag Manager (GTM), que es una solicitud específica de AJAX. El usuario puede eliminar esta AJAX y refactorizar su personalización con funcionalidad privada para reducir el número total de solicitudes al servidor.
* Compruebe si el titular de Adobe Commerce está habilitado pero no se utiliza. Es posible que tenga que [Deshabilitar la salida del titular de Adobe Commerce para mejorar el rendimiento del sitio](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26909).

### Lectura relacionada

Para obtener más información sobre contenido privado para clientes, [Contenido privado](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) en nuestra documentación para desarrolladores.
