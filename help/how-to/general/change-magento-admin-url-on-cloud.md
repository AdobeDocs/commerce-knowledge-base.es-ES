---
title: Cambiar la URL de administración en Adobe Commerce en la infraestructura en la nube
description: De forma predeterminada, la dirección URL [Commerce Admin](https://experienceleague.adobe.com/en/docs/commerce-admin/start/admin/admin) se establece en *&lt;domain_name&gt;/admin*. Este artículo muestra cómo cambiar la dirección URL.
exl-id: 6236370c-e0a2-45a6-a38f-12e219c540af
feature: Admin Workspace, Cloud
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Cambiar la URL de administración en Adobe Commerce en la infraestructura en la nube

De manera predeterminada, la dirección URL de [Commerce Admin](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin.html) está establecida en *&lt;domain\_name>/admin*. Este artículo muestra cómo cambiar la dirección URL.

## Método 1: cambio mediante el administrador

Lea los pasos: [Uso de una URL de administración personalizada > Cambio del administrador](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html#use-a-custom-admin-url) en nuestra guía de usuario.

## Método 2: Añadir la variable de entorno ADMIN\_URL

### Entorno de integración

En [Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html), agregue una nueva variable con:

**Nombre:** ADMIN\_URL **Valor:** nueva URL de administrador

* Para ver los pasos detallados, consulte [agregar variables de entorno](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-environment) en nuestra documentación para desarrolladores.
* Consulte también [variables de entorno](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html) en nuestra documentación para desarrolladores.

### Cuando Ensayo y producción no están disponibles en la consola en la nube

[Envíe un ticket de asistencia](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) solicitando agregar la variable ADMIN\_URL para su entorno de ensayo o producción.

Si se puede acceder a Ensayo y Producción desde la consola en la nube, agregue la variable de entorno como se describe en la sección *Entorno de integración* anterior.

### Adición de variables mediante CLI de nube

Puede agregar la variable ADMIN\_URL mediante el siguiente comando de CLI de nube (para main):

`magento-cloud variable:update ADMIN_URL --value newAdmin_A8v10 -e master --inheritable false`

Para obtener instrucciones más detalladas, consulte [Cambiar la URL de administración](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=en#change-the-admin-url) en el tema Variables de administración en la Guía de Commerce en la infraestructura de la nube.

Tenga en cuenta que el uso de la CLI de nube para cambiar la variable ADMIN\_URL déclencheur una reimplementación del entorno. Las variables se pueden heredar de forma predeterminada; para evitar la herencia, utilice las opciones del comando CLI de la nube para indicar que no desea que los entornos secundarios hereden el valor de la variable. Consulte el tema [Visibilidad](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) en Niveles variables en la Guía de Commerce en infraestructura de nube.
