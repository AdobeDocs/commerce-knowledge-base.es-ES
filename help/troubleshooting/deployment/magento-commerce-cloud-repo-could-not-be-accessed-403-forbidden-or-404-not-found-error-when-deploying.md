---
title: "No se pudo acceder a Adobe Commerce en el repositorio de la nube: Error 403 prohibido o 404 no encontrado al implementar"
description: "Este artículo explica cómo resolver el error de implementación fallido de Adobe Commerce en la infraestructura en la nube de forma similar a lo siguiente:"
exl-id: 2f72d80a-05b2-4908-8fa8-61d06885ed07
feature: Cloud, Deploy, Paas, Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 0%

---

# No se pudo acceder a Adobe Commerce en el repositorio en la nube: Error 403 prohibido o 404 no encontrado al implementar

Este artículo explica cómo resolver el error de implementación fallido de Adobe Commerce en la infraestructura en la nube de forma similar a lo siguiente:

&quot;*No se pudo tener acceso a la &#39;URL https://repo.magento.com/archives/magento/magento-cloud-configuration/magento-magento-cloud-configuration-x.x.x.x.zip&#39;: HTTP/1.1 403 Prohibido* &quot;. O el archivo &quot;*https://repo.magento.com/archives/magento/module-customer-segment/magento-module-customer-segment-102.0.5.0-patch2.zip&quot; no se pudo descargar (HTTP/1.1 404 No encontrado)*&quot;.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube 2.2.x, 2.3.x y 2.4.x

## Problema

Mensaje de error en la implementación que indica que no se pudo acceder a la URL del repositorio.

<u>Pasos a seguir</u>

Déclencheur la implementación manualmente o realizando una combinación, inserción o sincronización de su entorno.

<u>Resultado real</u>

La implementación se atasca. En el registro de errores de implementación de la interfaz de usuario del proyecto, aparece un mensaje de error similar al siguiente:

*&quot;No se pudo obtener acceso a la dirección URL &#39;https://repo.magento.com/archives/magento/magento-cloud-configuration/magento-magento-cloud-configuration-x.x.x.x.zip&#39;: HTTP/1.1 \[403 Prohibido o 404 No encontrado\]&quot;*.

(Haga clic en el icono &quot;Error&quot; en la interfaz de usuario del proyecto para ver el registro).

<u>Resultado esperado</u>

La implementación se ha completado correctamente.

## Causa

El error se debe a que las claves de autorización (claves de acceso) no son válidas, no se han especificado o no se han especificado correctamente.

Algunas de las razones por las que las claves no son válidas son:

* Ha generado las claves mediante su cuenta compartida.
* Su licencia se ha revocado anteriormente debido a problemas de pago.

>[!NOTE]
>
>Si descubre que esto se debe a un problema de facturación o de contrato vencido, póngase en contacto con el equipo de cuenta de Adobe para obtener ayuda y resolver este problema. Una vez reactivada la licencia, se restaurarán los derechos de asistencia e implementación.

## Solución

Siga estos pasos para resolver el problema con las claves de autorización (consulte las secciones siguientes para obtener más información sobre cada paso):

1. Obtenga las claves de autorización válidas (omita esta opción si está absolutamente seguro de que la clave es válida).
1. Agregue el valor de las claves en la variable `env:COMPOSER_AUTH` (o asegúrese de que el valor correcto esté allí) y compruebe si las claves se especifican de manera coherente en la variable en los niveles de proyecto y entorno, así como en el archivo `auth.json` (si existe) en la raíz del proyecto.
1. Actualice o elimine `auth.json`, para tener un solo lugar donde se configure la clave, si los valores de las claves de autorización no están especificados o tienen otro valor.

### 1. Obtenga claves de autorización válidas

Si utilizaba las claves creadas en la cuenta compartida, debe ponerse en contacto con el propietario de la licencia de Adobe Commerce, que le proporciona acceso y solicitar que genere las claves por usted.

Si se revocó su licencia anteriormente debido a problemas de pago y ha resuelto esos problemas y se ha renovado su licencia, debe [generar las nuevas claves de autenticación](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html).

### 2. Agregue el valor keys en la variable env:COMPOSER\_AUTH y compruebe si las mismas claves están especificadas en auth.json

Consulte las instrucciones y la información relacionada en [Prepare su sistema existente](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/overview) y [Agregue claves de autenticación](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/overview) en nuestra documentación para desarrolladores.

### 3. Actualice o elimine auth.json

A continuación se muestra una descripción paso a paso de cómo actualizar las claves de autorización:

1. Inicie sesión en el equipo que tenga las claves SSH de Adobe Commerce en la infraestructura de la nube.
1. Inicie sesión en el proyecto: `magento-cloud login`
1. Cree una rama para actualizar el código (en el siguiente ejemplo, el nombre de rama es `auth` y se crea a partir de la rama principal):     `magento-cloud environment:branch auth master`
1. Cambie al directorio raíz del proyecto.
1. Opcional: elimine `auth.json` si prefiere y continúe con el [paso 9](#step9).
1. Abra `auth.json` en un editor de texto.

   ```json
              {
                "http-basic":  {
                    "repo.magento.com": {
                        "username": "<public_key>",
                        "password": "<private_key>"
                        }
                      }
                    }
   ```

1. Añada las claves de autenticación correctas.
1. Guarde los cambios y salga del editor de texto.
1. Confirme y fusione los cambios:

   `git add -A`

   `git commit -m "<message>"`

   `git push origin master`
1. Espere a que se implemente el proyecto.
