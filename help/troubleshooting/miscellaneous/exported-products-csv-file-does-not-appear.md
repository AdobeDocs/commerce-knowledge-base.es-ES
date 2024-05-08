---
title: El archivo .csv de productos exportados no aparece
description: Este artículo proporciona una corrección del problema que se produce cuando se intenta exportar productos a un archivo .csv en el Administrador de Commerce, pero el archivo no aparece.
exl-id: 8e3bb65c-ea75-4af4-ad4b-4d94ab219bbb
feature: Cache, Data Import/Export, Products, Variables
role: Developer
source-git-commit: d55702ab97f3770d0ec71322f6c24448f0169ad4
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# El archivo .csv de productos exportados no aparece

Este artículo proporciona una corrección del problema que se produce cuando se intenta exportar productos a un archivo .csv en el Administrador de Commerce, pero el archivo no aparece.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, todo [versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problema

<u>Pasos a seguir</u>

Requisitos previos: **Añadir clave secreta a las direcciones URL** se establece en *Sí*. La opción se configura en el Administrador de Commerce en **Tiendas** > **Configuración** > **Avanzadas** > **Administrador** > **Seguridad**.

1. En el Administrador, vaya a **Sistema** > **Transferencia de datos** > **Exportar**.

   ![magento_export_products_2.3.4.png](assets/magento_export_products_2.3.4.png)

1. Seleccionar
   * **Tipo de entidad**: *Productos*
   * **Exportar formato de archivo**: *CSV*
   * **Chasis de campo**: dejar sin marcar.
1. Clic **Continuar**.
1. Se muestra el siguiente mensaje: *&quot;El mensaje se agrega a la cola, espere a obtener el archivo pronto&quot;*.

<u>Resultado esperado</u>

El archivo .csv con los productos exportados se muestra en la cuadrícula en un par de minutos.

<u>Resultado real</u>

El archivo .csv con los productos exportados no se mostrará en la cuadrícula en 10 minutos o más.

## Causa

Un problema conocido con la funcionalidad Exportar en la versión 2.3.2 del fragmento de aplicación de Adobe Commerce.

## Solución

Hay dos soluciones posibles para el problema:

* Deshabilite la opción Agregar clave secreta a la dirección URL.
* Ejecute el `bin/magento queue:consumers:start exportProcessor` comando manualmente y, opcionalmente, configúrelo para que lo ejecute cron.

Consulte los detalles de ambas opciones en los párrafos siguientes.

### Deshabilite la opción Agregar clave secreta a la dirección URL

1. En el Administrador, vaya a **Tiendas** > **Configuración** > **Avanzadas** > **Administrador** > **Seguridad**.
1. Configure las variables **Añadir clave secreta a las direcciones URL** opción para *No.*
1. Clic **Guardar configuración**.
1. Limpiar caché debajo de **Sistema** > **Herramientas** > **Administración de caché** o ejecutando    ```bash    bin/magento cache:clean``` o en el Administrador.

### Ejecute el comando de exportación manualmente y, opcionalmente, agréguelo como trabajo cron

Para obtener el archivo de exportación, ejecute el `bin/magento queue:consumers:start exportProcessor` comando. Después de ejecutar esto, el archivo debe mostrarse en la cuadrícula.


Para agregar el proceso como un trabajo cron de forma opcional, debe agregar la variable `CRON_CONSUMERS` a la `.magento.env.yaml` archivo.

#### Agregar proceso como trabajo cron (opcional)

1. Asegúrese de que su cron esté configurado. Consulte [Configuración de trabajos cron](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) para obtener más información.
1. Ejecute el siguiente comando para devolver una lista de consumidores de cola de mensajes:     `./bin/magento queue:consumers:list`
1. Añada lo siguiente a su `.magento.env.yaml` en el directorio raíz de la aplicación e incluya los consumidores que desee añadir. Por ejemplo, este es el consumidor necesario para el procesamiento de exportación:

   ```yaml
   stage:
       deploy:
           CRON_CONSUMERS_RUNNER:
               cron_run: true
               max_messages: 1000
               consumers:
                   - exportProcessor
   ```

   A continuación, inserte este archivo actualizado y vuelva a implementar su entorno. Referencia también [Agregar trabajos cron personalizados al proyecto](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#add-custom-cron-jobs-to-your-project) en nuestra documentación para desarrolladores.

>[!NOTE]
>
>Si no encuentra el `.magento.env.yaml` para su entorno y cree que se ha eliminado, debe crear un nuevo `.magento.env.yaml`. Podría estar vacío inicialmente, puede agregar información allí según sea necesario. Consulte los siguientes artículos: [Configuración de variables de entorno para la implementación](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) y [Variables de entorno](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) en nuestra documentación para desarrolladores.

>[!TIP]
>
>[Archivos YAML](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) distinguen entre mayúsculas y minúsculas y no permiten tabulaciones. Tenga cuidado de utilizar una sangría uniforme en todo el archivo .magento.env.yaml o es posible que la configuración no funcione según lo esperado. Los ejemplos de la documentación y del archivo de muestra utilizan sangría de dos espacios. Utilice el comando validate de ece-tools para comprobar la configuración.

>[!NOTE]
>
>En proyectos Pro de Adobe Commerce en infraestructura en la nube, la variable [función de autocrons](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=en#crontab) debe estar habilitado en la infraestructura en la nube de Adobe Commerce para poder agregar trabajos cron personalizados a los entornos de ensayo y producción mediante `.magento.app.yaml`. Si esta función no está habilitada, [crear una solicitud de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), para que se le añada el trabajo.
