---
title: El archivo .csv de productos exportados no aparece
description: Este artículo proporciona una corrección del problema que se produce cuando se intenta exportar el tipo de entidad deseado a un archivo .csv en el Administrador de Commerce, pero el archivo no aparece.
exl-id: 8e3bb65c-ea75-4af4-ad4b-4d94ab219bbb
feature: Cache, Data Import/Export, Products, Variables
role: Developer
source-git-commit: b6f1222918b027eaecda42b767e6f83b2cf0f5d0
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 0%

---

# El archivo .csv de productos exportados no aparece

Este artículo proporciona una solución al problema de que la exportación del tipo de entidad deseado a un archivo .csv en el administrador de Commerce hace que el archivo no aparezca.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, todas [versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problema

<u>Pasos a seguir</u>

Requisitos previos: la opción **Agregar clave secreta a las direcciones URL** está establecida en *Sí*. La opción está configurada en Commerce Admin en **Tiendas** > **Configuración** > **Avanzadas** > **Administración** > **Seguridad**.

1. En el Administrador, vaya a **Sistema** > **Transferencia de datos** > **Exportar**.

   ![magento_export_products_2.3.4.png](assets/magento_export_products_2.3.4.png)

1. Seleccionar
   * **Tipo de entidad**: La entidad que desea exportar
   * **Formato de archivo de exportación**: *CSV*
   * **Chasis de campo**: dejar sin marcar.
1. Haga clic en **Continuar**.
1. Se muestra el siguiente mensaje: *&quot;El mensaje se agrega a la cola, espere a obtener el archivo pronto&quot;*.

<u>Resultado esperado</u>

El archivo .csv que contiene el tipo de entidad deseado exportado se muestra en la cuadrícula en un par de minutos.

<u>Resultado real</u>

El archivo .csv que contiene el tipo de entidad deseado exportado no se muestra en la cuadrícula en 10 minutos o más.

## Causa

Un problema conocido con la funcionalidad Exportar en la versión 2.3.2 del fragmento de aplicación de Adobe Commerce.

## Solución

Hay dos soluciones posibles para el problema:

* Deshabilite la opción Agregar clave secreta a la dirección URL.
* Ejecute el comando `bin/magento queue:consumers:start exportProcessor` manualmente y, opcionalmente, configúrelo para que lo ejecute cron.

Consulte los detalles de ambas opciones en los párrafos siguientes.

### Deshabilite la opción Agregar clave secreta a la dirección URL

1. En el Administrador, vaya a **Tiendas** > **Configuración** > **Avanzado** > **Administrador** > **Seguridad**.
1. Establezca la opción **Agregar clave secreta a las direcciones URL** en *No.*
1. Haga clic en **Guardar configuración**.
1. Limpie la caché en **Sistema** > **Herramientas** > **Administración de caché** o ejecutando    ```bash    bin/magento cache:clean``` o en el administrador.

### Ejecute el comando de exportación manualmente y, opcionalmente, agréguelo como trabajo cron

Para obtener el archivo de exportación, ejecute el comando `bin/magento queue:consumers:start exportProcessor`. Después de ejecutar esto, el archivo debe mostrarse en la cuadrícula.


Para agregar el proceso como un trabajo cron de forma opcional, debe agregar la variable `CRON_CONSUMERS` al archivo `.magento.env.yaml`.

#### Agregar proceso como trabajo cron (opcional)

1. Asegúrese de que su cron esté configurado. Consulte [Configurar trabajos cron](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) para obtener más información.
1. Ejecute el siguiente comando para devolver una lista de consumidores de cola de mensajes:     `./bin/magento queue:consumers:list`
1. Agregue lo siguiente al archivo `.magento.env.yaml` en el directorio raíz de la aplicación e incluya a los consumidores que desee agregar. Por ejemplo, este es el consumidor necesario para el procesamiento de exportación:

   ```yaml
   stage:
       deploy:
           CRON_CONSUMERS_RUNNER:
               cron_run: true
               max_messages: 1000
               consumers:
                   - exportProcessor
   ```

   A continuación, inserte este archivo actualizado y vuelva a implementar su entorno. También haga referencia a [Agregar trabajos cron personalizados a su proyecto](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#add-custom-cron-jobs-to-your-project) en nuestra documentación para desarrolladores.

>[!NOTE]
>
>Si no encuentra el archivo `.magento.env.yaml` para su entorno y cree que se eliminó, debe crear un nuevo `.magento.env.yaml`. Podría estar vacío inicialmente, puede agregar información allí según sea necesario. Consulte los siguientes artículos: [Configurar variables de entorno para la implementación](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) y [Variables de entorno](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) en nuestra documentación para desarrolladores.

>[!TIP]
>
>[Los archivos YAML](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) distinguen entre mayúsculas y minúsculas y no permiten tabulaciones. Tenga cuidado de utilizar una sangría uniforme en todo el archivo .magento.env.yaml o es posible que la configuración no funcione según lo esperado. Los ejemplos de la documentación y del archivo de muestra utilizan sangría de dos espacios. Utilice el comando validate de ece-tools para comprobar la configuración.

>[!NOTE]
>
>En proyectos Pro de Adobe Commerce en la infraestructura en la nube, la función [auto-crons](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=en#crontab) debe estar habilitada en tu Adobe Commerce en la infraestructura en la nube para que puedas agregar trabajos cron personalizados a entornos de Ensayo y Producción usando `.magento.app.yaml`. Si esta característica no está habilitada, [cree un vale de soporte técnico](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para que se agregue el trabajo por usted.
