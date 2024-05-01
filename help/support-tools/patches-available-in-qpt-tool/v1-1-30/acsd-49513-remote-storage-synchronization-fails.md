---
title: "ACSD-49513: La sincronización del almacenamiento remoto falla"
description: Aplique el parche ACSD-49513 para corregir el problema de Adobe Commerce en el que la sincronización del almacenamiento remoto falla debido a archivos de 0 bytes.
exl-id: fce5f60f-d21f-40cd-8d8a-a1a26e0fbe75
feature: Iaas, Storage
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-49513: la sincronización de almacenamiento remoto falla debido a archivos de 0 bytes

El parche de ACSD-49513 soluciona el problema en el que la sincronización del almacenamiento remoto falla debido a archivos de 0 bytes. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 está instalado. El ID del parche es ACSD-49513. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.4-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La sincronización del almacenamiento remoto falla debido a archivos de 0 bytes.

<u>Pasos a seguir</u>:

1. Configure AWS S3 como almacenamiento remoto.
1. Ejecutar `[bin/magento remote-storage:sync]` para asegurarse de que la sincronización funciona correctamente al principio.
1. Cree un archivo de 0 bytes dentro de `[pub/media]`.
1. Ejecutar `[bin/magento remote-storage:sync]` otra vez.

<u>Resultados esperados</u>:

Dado que AWS S3 acepta archivos de 0 bytes en la inserción directa S3, no hay error.

<u>Resultados reales</u>:

Se produce el siguiente error:

```PHP
Uploading media files to remote storage.
In File.php line 387:
  The file or directory "pub/media/xxxx.file" cannot be copied to "*.amazonaws.com/media/xxxx.file"
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Pasos adicionales necesarios tras la instalación del parche

(Esta sección es opcional; es posible que se requieran algunos pasos después de aplicar el parche para solucionar el problema). 

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
