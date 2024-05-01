---
title: "ACSD-47657: agrega un mecanismo de almacenamiento en caché para las credenciales de AWS"
description: Aplique el parche ACSD-47657 para corregir el problema de Adobe Commerce que se produce durante una carga alta de solicitudes a AWS S3 añadiendo un mecanismo de almacenamiento en caché para las credenciales de AWS.
feature: Cache
role: Admin, Developer
exl-id: d5822082-c656-45bf-b192-9cc8007b82a2
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# ACSD-47657: agrega un mecanismo de almacenamiento en caché para las credenciales de AWS

El parche ACSD-47657 corrige el problema que se produce durante una carga alta de solicitudes a AWS S3 al agregar un mecanismo de almacenamiento en caché para las credenciales de AWS. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39 está instalado. El ID del parche es ACSD-47657. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Agregar un mecanismo de almacenamiento en caché para las credenciales de AWS recuperadas de AWS para la configuración de EC2.

<u>Pasos a seguir</u>:

1. Habilite el almacenamiento en bloque de AWS S3 para Adobe Commerce:

   ```
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="magentopubmedia-prod" --remote-storage-region="aws-west" --no-interaction
   bin/magento config:set 
   system/media_storage_configuration/media_database 0 
   bin/magento cache:flush
   ```

1. Ejecutar sincronización:

   ```
   bin/magento remote-storage:sync
   ```

<u>Resultados esperados</u>:

La sincronización finaliza correctamente.

<u>Resultados reales</u>:

En aproximadamente una hora, se produce el siguiente error:

```
    report.CRITICAL: Aws\Exception\CredentialsException: Error retrieving credentials from the instance profile metadata service. (cURL error 28: Connection timed out after 1001 milliseconds) (see https://curl.haxx.se/libcurl/c/libcurl-errors.html) 
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
