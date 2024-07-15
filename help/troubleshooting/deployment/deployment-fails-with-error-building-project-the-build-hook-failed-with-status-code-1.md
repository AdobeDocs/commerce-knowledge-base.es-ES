---
title: 'La implementación falla con "Error al crear el proyecto: Error del vínculo de compilación con el código de estado 1"'
description: 'Este artículo habla sobre las causas y las soluciones del problema de infraestructura en la nube de Adobe Commerce, donde la fase de compilación del proceso de implementación falla y el mensaje de error se resume con: *"Error al crear el proyecto: El vínculo de compilación falló con el código de estado 1"*.'
exl-id: add1cdac-dbcb-4c55-8bc2-c1f27e24aadb
feature: Build, Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '750'
ht-degree: 0%

---

# La implementación falla con &quot;Error al crear el proyecto: Error del vínculo de compilación con el código de estado 1&quot;

Este artículo trata sobre las causas y soluciones del problema de infraestructura en la nube de Adobe Commerce, donde la fase de compilación del proceso de implementación falla y el mensaje de error se resume con: *&quot;Error al crear el proyecto: El vínculo de compilación falló con el código de estado 1&quot;*.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, todas las versiones

## Problema

<u>Pasos a seguir</u>:

Almacene en déclencheur la implementación manualmente o realizando una combinación, inserción o sincronización de su entorno.

<u>Resultado esperado</u>:

La implementación se ha completado correctamente.

<u>Resultado real</u>:

1. La fase de creación falla y todo el proceso de implementación se queda atascado.
1. En el registro de errores de implementación, el mensaje de error termina con: *&quot;Error al crear el proyecto: Error en el vínculo de generación con el código de estado 1. Compilación anulada&quot;.*

## Causa

Existen varias razones por las que la creación de entornos falla. Normalmente, en el registro de implementación verá un mensaje de error largo, donde la primera parte sería más específica con respecto al motivo y la conclusión sería *&quot;Error al crear el proyecto: El vínculo de compilación falló con el código de estado 1. Compilación anulada&quot;.*

Si mira más de cerca la primera parte específica del problema, le ayudará a identificar el problema. Estas son las más comunes y la siguiente sección proporciona soluciones para ellas:

* No hay espacio de almacenamiento disponible.
* Configuración de ECE-Tools incorrecta.
* El parche que está intentando aplicar no es compatible con su versión de Adobe Commerce o está en conflicto con otros parches aplicados a sus personalizaciones.
* Los problemas con el código de módulos personalizados impiden la compilación correctamente.

## Solución

* Compruebe que haya suficiente espacio de almacenamiento. Para obtener información sobre cómo comprobar el espacio disponible, consulte el artículo [Comprobar el espacio en disco en el entorno de la nube mediante CLI](/help/how-to/general/check-disk-space-on-cloud-environment-using-cli.md). Puede considerar la posibilidad de limpiar los directorios de registro o aumentar el espacio en disco.
* Asegúrese de que ECE-Tools está configurado correctamente.
* Compruebe si es el parche el que causa la avería. Resuelva el conflicto o comuníquese con [Soporte técnico de Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Consulte a continuación para obtener más información.
* Compruebe si es la extensión personalizada la que está causando el problema. Resuelva el conflicto o póngase en contacto con los desarrolladores de la extensión para la solución.

En los párrafos siguientes se proporcionan más detalles.

### Limpieza de registros o aumento de espacio

Directorios que se deben considerar para la limpieza:

* `var/log`
* `var/report`
* `var/debug/`
* `var`

Para obtener más información sobre cómo aumentar el espacio en disco si utiliza la arquitectura del plan de inicio de la infraestructura en la nube de Adobe Commerce, consulte [Aumento del espacio en disco para el entorno de integración en la nube](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md). Las mismas instrucciones se pueden utilizar para aumentar el espacio de Adobe Commerce en la infraestructura en la nube. Para Pro Production/Staging, debes enviar un ticket al [Soporte técnico de Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) y solicitar más espacio en el disco. Pero es monitoreado por Platform. Pero, por lo general, no tendrá que lidiar con esto en la arquitectura de ensayo/producción de Pro, ya que Adobe Commerce supervisa estos parámetros por usted y le alerta o toma medidas según el contrato.

### Asegúrese de que las herramientas ECE están correctamente configuradas

1. Asegúrese de que los vínculos de compilación se definen correctamente en el archivo `magento.app.yaml`. Si utiliza Adobe Commerce 2.2.X, los vínculos de creación deben definirse de la siguiente manera:

   ```yaml
   # We run build hooks before your application has been packaged.
   build: |
       php ./vendor/bin/ece-tools build
   # We run deploy hook after your application has been deployed and started.
   deploy: |
       php ./vendor/bin/ece-tools deploy
   ```

   Use el artículo [Actualizar a ece-tools](https://devdocs.magento.com/guides/v2.3/cloud/project/ece-tools-upgrade-project.html) para referencia.

1. Asegúrese de que el paquete ECE-tools esté presente en el archivo `composer.lock` ejecutando el siguiente comando:    <pre><code class="language-bash">grep &#39;<code class="language-yaml">&quot;name&quot;: &quot;magento/ece-tools&quot;</code>&#39; composer.lock</code></pre>    Si se especifican, la respuesta tendría el siguiente aspecto:    ```bash    "name": "magento/ece-tools",    "version": "2002.0.20",    ```

Consulte el artículo [Actualizar a ece-tools](https://devdocs.magento.com/guides/v2.3/cloud/project/ece-tools-upgrade-project.html) para obtener una referencia.

### ¿El parche está causando el problema?

Si es el parche aplicado el que impide que el entorno se cree correctamente, verá algo similar a lo siguiente en el registro de implementación:

```bash
%patch_name%.composer.patch
[2019-02-19 18:12:59] CRITICAL:
....
[2019-02-19 18:12:59] CRITICAL: Command git apply --check --reverse /app/m2-hotfixes/%patch_name%.composer.patch returned code 1
...
W:
W: Command git apply --check --reverse /app/m2-hotfixes/%patch_name%.composer.patch returned code 1
W:
W:
W: build
...
E: Error building project: The build hook failed with status code 1. Aborted build.
```

Estos mensajes de error significan que el parche que está intentando aplicar se ha creado para una versión diferente de Adobe Commerce o que está en conflicto con las personalizaciones o con los parches aplicados anteriormente. Intente resolver el conflicto o póngase en contacto con el [Soporte técnico de Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### ¿La extensión de está causando el problema?

Si la extensión personalizada impide que el entorno se genere correctamente, verá los nombres de los módulos personalizados mencionados en el registro de implementación, junto con el conflicto particular causado por este módulo. Resuelva el conflicto o póngase en contacto con los desarrolladores de la extensión para la solución.

### Asegúrese de que se aplican los cambios

Confirme y envíe los cambios. Esto almacenará la implementación en déclencheur automáticamente.
