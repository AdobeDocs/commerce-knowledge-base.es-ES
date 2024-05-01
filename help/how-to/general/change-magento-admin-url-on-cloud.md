---
title: Cambiar la URL de administración en Adobe Commerce en la infraestructura en la nube
description: De forma predeterminada, la dirección URL [Commerce Admin](https://docs.magento.com/m2/ee/user_guide/stores/admin.html) se establece en *&lt;domain\_name&gt;/admin*. Este artículo muestra cómo cambiar la dirección URL.
exl-id: 6236370c-e0a2-45a6-a38f-12e219c540af
feature: Admin Workspace, Cloud
source-git-commit: 04dba4e2adeaaa7649b817444024bf96e7830ad3
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Cambiar la URL de administración en Adobe Commerce en la infraestructura en la nube

De forma predeterminada, la variable [Administrador de Commerce](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin.html) La URL se ha establecido en *&lt;domain _name=&quot;&quot;>/admin*. Este artículo muestra cómo cambiar la dirección URL.

## Método 1: cambio mediante el administrador

Lea los pasos: [Uso de una URL de administración personalizada > Cambiar del administrador](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html#use-a-custom-admin-url) en nuestra guía del usuario.

## Método 2: Añadir la variable de entorno ADMIN\_URL

### Entorno de integración

Desde el [Consola de nube](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html), agregue una nueva variable con:

**Nombre:** ADMIN\_URL **Valor:** nueva URL de administrador

* Para ver los pasos detallados, consulte [agregar variables de entorno](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-environment) en nuestra documentación para desarrolladores.
* Consulte también [variables de entorno](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html) en nuestra documentación para desarrolladores.

### Cuando Ensayo y producción no están disponibles en la consola en la nube

[Enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) solicitando agregar la variable ADMIN\_URL para el entorno de ensayo o producción.

Si puede acceder a Ensayo y Producción desde la consola en la nube, agregue la variable de entorno como se describe en la *Entorno de integración* sección anterior.

### Adición de variables mediante CLI de nube

Puede agregar la variable ADMIN\_URL mediante el siguiente comando de CLI de nube (para main):

`magento-cloud variable:update ADMIN_URL --value newAdmin_A8v10 -e master --inheritable false`

Para obtener instrucciones más detalladas, consulte [Cambio de la URL de administración](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=en#change-the-admin-url) en el tema Variables de administración de la Guía de Commerce en la infraestructura de la nube.

Tenga en cuenta que el uso de la CLI de nube para cambiar la variable ADMIN\_URL déclencheur una reimplementación del entorno. Las variables se pueden heredar de forma predeterminada; para evitar la herencia, utilice las opciones del comando CLI de la nube para indicar que no desea que los entornos secundarios hereden el valor de la variable. Consulte la [Visibilidad](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) tema en Niveles de variable en la Guía de Commerce en infraestructura de nube.
