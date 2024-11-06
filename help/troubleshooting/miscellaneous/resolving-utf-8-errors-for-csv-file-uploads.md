---
title: Solución de errores UTF-8 para cargas de archivos CSV
description: Este artículo proporciona una corrección para los casos en los que se recibe el mensaje de error "Los archivos CSV deben utilizar la codificación UTF-8". Este mensaje de error significa que el archivo que intenta cargar contiene caracteres no válidos o no permitidos. Aunque la codificación UTF-8 permite [la mayoría de los caracteres](https://www.fileformat.info/info/charset/UTF-8/list.htm), algunos no son compatibles con Magento BI.
exl-id: 88d8e0b8-152e-4a6d-bc44-3b285e0eb0c3
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Solución de errores UTF-8 para cargas de archivos CSV

Este artículo proporciona una corrección para los casos en los que se recibe el mensaje de error &quot;Los archivos CSV deben utilizar la codificación UTF-8&quot;. Este mensaje de error significa que el archivo que intenta cargar contiene caracteres no válidos o no permitidos. Aunque la codificación UTF-8 permite [la mayoría de los caracteres](https://www.fileformat.info/info/charset/UTF-8/list.htm), algunos no son compatibles con el BI de Magento.

Para solucionar el problema, deberá cambiar la codificación del archivo. Volver a guardar el archivo con la codificación adecuada suele resolver el problema, pero tenga en cuenta que puede perder información (por ejemplo, los caracteres no permitidos pueden perderse) al hacerlo.

Se recomienda usar [Texto sublime](https://www.sublimetext.com/2) para guardar y codificar el archivo.

1. Abra el archivo en Microsoft Excel, Google Docs, Apple Numbers o el programa que desee.
1. Haga clic en&#x200B; **Archivo** > **Guardar como**&#x200B; y seleccione el formato&#x200B; **Valores separados por comas (.csv)** para guardar el archivo.
1. Abra el archivo CSV en Texto sublime.
1. En Texto sublime, vaya a&#x200B; **Archivo** > **Guardar con codificación** > **UTF-8\*&#x200B;** . Esto guardará el archivo CSV con codificación UTF-8.    ![csv_file_UTF-8_sublime_3.2.2_magento_BI.png](assets/csv_file_UTF-8_sublime_3.2.2_magento_BI.png)
1. [Cargue los datos](https://experienceleague.adobe.com/en/docs/commerce-business-intelligence/mbi/analyze/connecting/using-file-uploader) (en nuestra guía del usuario) a una nueva tabla en Magento BI.
