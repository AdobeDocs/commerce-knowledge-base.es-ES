---
title: Configuración de la conexión de Adobe Commerce Intelligence para proyectos existentes de Cloud Starter
description: Este artículo proporciona una solución para cuando desee configurar la conexión de Adobe Commerce Intelligence para un proyecto existente de Cloud Starter.
feature: Commerce Intelligence
role: Developer
exl-id: 56f6ad64-729d-4e3a-93a9-da1b91bc5c1d
source-git-commit: b75328202952bf4c8f57ddc538b5c9e4318b2001
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---

# Configuración de la conexión de Adobe Commerce Intelligence para proyectos existentes de Cloud Starter

>[!NOTE]
>
>Adobe Commerce Intelligence se conocía anteriormente como Magento Business Intelligence (MBI).

Este artículo proporciona una solución para cuando desee configurar la conexión de Adobe Commerce Intelligence para un proyecto existente de Cloud Starter.

## Productos y versiones afectados

Adobe Commerce en cloud starter (todas las versiones)

## Problema

Desea configurar la conexión de Commerce Intelligence para un proyecto existente de Cloud Starter.

>[!NOTE]
>
>Adobe ya no admite nuevas suscripciones a Cloud Starter, pero si tiene un proyecto de Starter existente, deberá seguir los pasos que se indican a continuación para configurar su conexión.

## Solución

Para activar Commerce Intelligence para proyectos de Cloud Starter, cree una cuenta de Commerce Intelligence, una clave SSH y, finalmente, conéctese a la base de datos de Adobe Commerce.

Siga estos pasos:

1. Cree su cuenta de Adobe Commerce Intelligence:

   * Vaya a [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login).
   * Vaya a **[!UICONTROL My Account]** > **[!UICONTROL My MBI Instances]**.
   * Haga clic en **[!UICONTROL Create Instance]**. Si no ve este botón, póngase en contacto con el administrador de éxito del cliente o con el asesor técnico del cliente.
   * Seleccione su suscripción a Cloud Starter. Si solo tiene una suscripción a Cloud Starter, esta se selecciona automáticamente.
   * Haga clic en **[!UICONTROL Continue]**.
   * Introduzca su información para crear su cuenta de.

   ![Crear cuenta MBI](/help/troubleshooting/miscellaneous/assets/create_mbi_account.png)

   * Vaya a la bandeja de entrada y verifique la dirección de correo electrónico.

   ![Verificar dirección de correo electrónico](/help/troubleshooting/miscellaneous/assets/verify_email_address_mbi.png)

   * Cree una contraseña.

   ![Crear una contraseña](/help/troubleshooting/miscellaneous/assets/create_password_mbi.png)

   * Después de crear la cuenta, tendrá la opción de agregar usuarios a la nueva cuenta. Ahora se pueden añadir administradores técnicos para llevar a cabo los siguientes pasos.

   ![Agregar usuarios](/help/troubleshooting/miscellaneous/assets/add_users_mbi.png)

1. Introduce información sobre tu tienda para establecer tus preferencias.

   ![Agregar información de tienda](/help/troubleshooting/miscellaneous/assets/add_store_info_mbi.png)

   Debe recopilar cierta información antes de poder conectar la base de datos para el tercer paso del flujo de incorporación. Rellenará la página *[!UICONTROL Connect your database]* en el paso 9.

1. Cree un usuario de Commerce Intelligence dedicado.

   * Cree un nuevo usuario en [account.adobe.com](https://account.adobe.com/).
   * Vaya a [https://accounts.magento.com/customer/account/](https://accounts.magento.com/customer/account/) para generar su cuenta de Adobe Commerce.
   * ¿Por qué un nuevo usuario? Adobe Commerce Intelligence necesita que se agregue un usuario al proyecto para recuperar continuamente nuevos datos que se transferirán al almacén de datos de Commerce Intelligence de la cuenta. Este usuario servirá como esa conexión. Añadir este usuario al proyecto se realizará en el paso 4.
   * El motivo de tener un usuario de Commerce Intelligence dedicado es evitar que el usuario agregado se desactive o elimine de forma involuntaria y detenga la conexión de Commerce Intelligence.

1. Agregue el usuario recién creado al entorno principal del proyecto como *Colaborador*.

   ![Agregar usuario como colaborador](/help/troubleshooting/miscellaneous/assets/contributor_user_mbi.png)

1. Obtenga sus claves SSH de Commerce Intelligence.

   * Vaya a la página **[!UICONTROL Connect your database]** de la interfaz de usuario configurada de Commerce Intelligence y desplácese hacia abajo hasta **[!UICONTROL Encryption settings]**.
   * Para el campo **[!UICONTROL Encryption Type]**, elija **[!UICONTROL SSH Tunnel]**.
   * En el menú desplegable, puede copiar y pegar la clave pública de Magento BI Essentials proporcionada.

   ![Configuración de cifrado](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

1. Añada la nueva clave pública de Magento BI Essentials al usuario de Commerce Intelligence creado en el paso 5.

   * Vaya a [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login). Inicie sesión con la información de inicio de sesión de la cuenta para el nuevo usuario de Commerce Intelligence creado. A continuación, vaya a la ficha **[!UICONTROL Account Settings]**.
   * Desplácese hacia abajo por la página y expanda la lista desplegable para claves SSH. Luego haga clic en **[!UICONTROL Add a public key]**.

   ![Agregar una clave pública](/help/troubleshooting/miscellaneous/assets/add_public_key_mbi.png)

   * Añada la clave pública SSH de MBI Essentials del Magento desde arriba.

   ![Añadir clave pública SSH](/help/troubleshooting/miscellaneous/assets/add_ssh_key_mbi.png)

1. Proporcione las credenciales de MySQL de Business Intelligence Essentials.

   * Actualice su `.magento/services.yaml`.

   ```
   mysql:
    type: mysql:10.0
    disk: 2048
    configuration:
        schemas:
            - main
        endpoints:
            mysql:
                default_schema: main
                privileges:
                    main: admin
            mbi:
                default_schema: main
                privileges:
                    main: ro
   ```

   * Actualice su `.magento.app.yaml`.

   ```
   relationships:
            database: "mysql:mysql"
            mbi: "mysql:mbi"
            redis: "redis:redis"
   ```

1. Obtenga información para conectar la base de datos a Commerce Intelligence.

   Ejecute `echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 --decode | json_pp` para obtener información sobre cómo conectar la base de datos.

   Debe recibir información similar a la siguiente:

   ```
   "mbi" : [
              {
                 "scheme" : "mysql",
                 "rel" : "mbi",
                 "cluster" : "vfbfui4vmfez6-master-7rqtwti",
                 "query" : {
                    "is_master" : true
                 },
                 "ip" : "169.254.169.143",
                 "path" : "main",
                 "host" : "mbi.internal",
                 "hostname" : "3m7xizydbomhnulyglx2ku4wpq.mysql.service._.magentosite.cloud",
                 "username" : "mbi",
                 "service" : "mysql",
                 "port" : 3306,
                 "password" : "[password]"
              }
           ],
   ```

1. Conecte la base de datos de Adobe Commerce.

   ![Conecte su base de datos de Adobe Commerce](/help/troubleshooting/miscellaneous/assets/connect_magento_database_mbi.png)

   *Entradas*:

   * Nombre de integración: [Elija un nombre para su integración.]
   * Host: `mbi.internal`
   * Puerto: 3306
   * Nombre de usuario: mbi
   * Contraseña: [se proporcionó la contraseña de entrada en el resultado del paso 8.]
   * Nombre de base de datos: main
   * Prefijos de tabla: [dejar en blanco si no hay prefijos de tabla]

1. Establezca su [!UICONTROL Timezone Settings].

   ![Configuración de zona horaria](/help/troubleshooting/miscellaneous/assets/timezone_settings_mbi.png)

   *Entradas*

   * Base de datos: Zona horaria: UTC
   * Zona horaria deseada: [Elija la zona horaria en la que desea que se muestren los datos.]

1. Obtenga información para la configuración de cifrado.

   * La IU del proyecto proporciona una cadena de acceso SSH. Esta cadena se puede usar para recopilar la información necesaria para la dirección remota y el nombre de usuario al configurar su **[!UICONTROL Encryption settings]**. Seleccione **[!UICONTROL SSH]** para ver su nombre de usuario y dirección remota. La cadena de texto antes de *@* es su nombre de usuario y la cadena de texto después de *@* es su dirección remota.

   ![Obtener acceso al sitio principal](/help/troubleshooting/miscellaneous/assets/access_site_mbi.png)

1. Escriba información para su [!UICONTROL Encryption Settings].

   ![Configuración de cifrado](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

   *Entradas*

   * Tipo de cifrado: túnel SSH
   * Dirección remota: ssh.us-3.magento.cloud
   * Nombre de usuario: vfbfui4vmfez6-master-7rqtwti-mymagento
   * Puerto: 22

1. Haga clic en **[!UICONTROL Save Integration]**.
1. Ahora se ha conectado correctamente a su cuenta de Commerce Intelligence Essentials.
1. Si es cliente de Adobe Commerce Intelligence Pro, póngase en contacto con el administrador de éxito del cliente o con el asesor técnico del cliente para coordinar los siguientes pasos.
