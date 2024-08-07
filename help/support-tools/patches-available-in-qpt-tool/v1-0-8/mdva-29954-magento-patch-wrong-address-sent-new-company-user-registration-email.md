---
title: "MDVA-29954: dirección incorrecta enviada por correo electrónico para el registro de nuevo usuario de la empresa"
description: El parche MDVA-29954 resuelve el problema por el que los correos electrónicos "Nueva solicitud de registro de empresa" y "Se le ha vinculado a una empresa" se envían desde la dirección de correo electrónico incorrecta. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.
exl-id: 9b3d1b93-3fe6-40a0-a68a-3e3d789c6d66
feature: B2B, Communications, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# MDVA-29954: dirección incorrecta enviada por correo electrónico para el registro de nuevos usuarios de la empresa

El parche MDVA-29954 resuelve el problema por el que los correos electrónicos &quot;Nueva solicitud de registro de empresa&quot; y &quot;Se le ha vinculado a una empresa&quot; se envían desde la dirección de correo electrónico incorrecta. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.3.5-p2, 2.4.0 y 2.4.1.

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Requisitos previos</u>:

Instale Adobe Commerce con B2B, con **características B2B** y **compañía** habilitadas.

<u>Pasos a seguir</u>:

1. Haga clic en el menú desplegable **Crear cuenta** de la tienda y seleccione **Crear nueva cuenta de compañía**.
1. Rellene los campos obligatorios y registre la cuenta.
1. Habilite **Compañía** desde el backend (**Cliente** > **Compañías**).
1. Compruebe la dirección de correo electrónico que utilizó para registrarse.
1. Establezca la **contraseña de administrador de la compañía** siguiendo las instrucciones que se enviaron por correo electrónico.
1. Inicie sesión en el front-end con **la contraseña de administrador de la compañía**.
1. Crear un nuevo **usuario de la compañía** en **Mi cuenta** > **usuarios de la compañía** > **Agregar nuevo usuario**.
1. Vaya a **Tiendas** > **Configuraciones** > **Direcciones de correo electrónico generales del almacén** > **Contacto general** y compruebe **Correo electrónico del remitente**.
1. Vaya al correo electrónico que utilizó para registrar a **Nuevo usuario** en el paso 7.

<u>Resultados esperados</u>:

El correo electrónico &quot;Se te ha vinculado a una empresa&quot; se envía desde una dirección de correo electrónico con el mismo valor que para **Correo electrónico del remitente** en el paso 8.

<u>Resultados reales</u>:

El correo electrónico &quot;Se te ha vinculado a una compañía&quot; se envía desde el correo electrónico **Administrador de compañías**.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
