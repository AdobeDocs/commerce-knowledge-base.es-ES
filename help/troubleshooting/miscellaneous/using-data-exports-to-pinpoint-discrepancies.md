---
title: Uso de las exportaciones de datos para detectar discrepancias
description: Este artículo proporciona soluciones para la resolución de discrepancias en los datos de BI de Magento. Las exportaciones de datos son una herramienta útil para comparar los datos de BI de Magento con los datos de origen a fin de detectar discrepancias de datos en los informes, especialmente si la [lista de comprobación de diagnóstico de discrepancias de datos](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy) no le ayudó a identificar el problema. Este artículo le guiará por un ejemplo en la vida real de cómo se pueden identificar las discrepancias de datos mediante las exportaciones de datos.
exl-id: b42d585c-ad8c-4685-9ad4-a13686566f18
feature: Commerce Intelligence, Data Import/Export
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '1300'
ht-degree: 0%

---

# Uso de las exportaciones de datos para detectar discrepancias

Este artículo proporciona soluciones para la resolución de discrepancias en los datos de BI de Magento. Las exportaciones de datos son una herramienta útil para comparar los datos de BI de Magento con los datos de origen con el fin de detectar discrepancias de datos en los informes, especialmente si la [lista de comprobación de diagnóstico de discrepancias de datos](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy) no le ayudó a identificar el problema. Este artículo le guiará por un ejemplo en la vida real de cómo se pueden identificar las discrepancias de datos mediante las exportaciones de datos.

Veamos este análisis, por ejemplo:

![](assets/Exports_Discrepancies_1.png)

Hay una caída sospechosa en noviembre de 2014. ¿500.780,94 dólares en ingresos? Eso no suena bien. Ha confirmado que se muestran más ingresos para el mes de noviembre de 2014 en la base de datos de origen y ha comprobado que la métrica **Ingresos** utilizada en este informe está definida correctamente. Parece que los datos del almacén de datos de Magento BI están incompletos, lo que se puede confirmar mediante una exportación de datos.

## Exportación de datos {#export}

Para empezar, haga clic en el engranaje en la esquina superior derecha del gráfico y, a continuación, seleccione la opción Exportación sin procesar en el menú desplegable. Esto le proporcionará una exportación sin procesar de los datos subyacentes al gráfico.

![](assets/Export_Discrepancies_5.gif)

En el menú **Exportación de datos sin procesar**, puede seleccionar la tabla desde la que desea exportar junto con las columnas que desea incluir en la exportación. Los filtros también se pueden aplicar al conjunto de resultados.

En nuestro ejemplo, la métrica **Ingresos** usada en este informe usa el campo **pedido\_total** definido en la tabla **`orders`**, usando la **fecha** como marca de tiempo. En nuestra exportación, queremos incluir todos los valores de **order\_id** para noviembre de 2014 y sus **order\_total** . La métrica **Ingresos** no usa ningún filtro, pero agregaremos un filtro a la exportación para limitar el conjunto de resultados a noviembre de 2014.

Este es el aspecto del menú Exportación de datos sin procesar para este ejemplo:

![](assets/Exports_Discrepancies_2.png)

Haga clic en Exportar datos para comenzar la exportación. Se mostrará una ventana con los detalles de la exportación, incluido el estado. La preparación de la exportación tarda unos minutos, por lo que es un buen momento para realizar una extracción análoga de los datos de origen para noviembre de 2014, incluidos **date, order\_id** y **order\_total** . Abriremos este archivo en Excel y lo dejaremos arriba, ya que volveremos a él en breve.

Cuando aparezca el botón Descargar en la ventana Exportaciones de datos sin procesar, haga clic en él para descargar el archivo zip que contiene el archivo CSV.

![](assets/Export_Discrepancies_6.png)

En este punto, necesitamos poner todos los datos en una hoja para encontrar el problema. Importaremos el archivo CSV (la exportación desde Magento BI) en una hoja diferente del archivo de Excel que contiene los datos de origen.

## Localización del problema {#pinpoint}

Ahora que todos los datos están en un solo lugar, podemos buscar el origen de la discrepancia. Comparar el número de filas en cada hoja nos ayudará a identificar el problema. Vamos a echar un vistazo más de cerca a cada situación.

### Ambas hojas contienen el mismo número de filas

Si ambos sistemas tienen el mismo recuento de filas y la métrica **Ingresos** no coincide con los datos de origen, el **pedido\_total** debe estar desactivado en algún lugar. Es posible que el campo **order\_total** se haya actualizado en la base de datos de origen y que el BI del Magento no esté recogiendo estos cambios.

Para confirmarlo, compruebe de nuevo si la columna **order\_total** se está comprobando o no. Vaya al Administrador de Datas Warehouse y haga clic en la tabla **`orders`**. Verá la [frecuencia de repetición de comprobación](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html) en la lista &#39;¿Cambios?&#39; columna. El campo **pedido\_total** debe configurarse para que vuelva a comprobarse con la frecuencia con la que se espera que cambie; si no lo es, continúe y configúrelo en la frecuencia de comprobación que desee.

### ![](assets/Export_Discrepancies_4.gif)

Si la frecuencia de repetición de la comprobación ya está ajustada correctamente, significa que hay otra anomalía. Consulte [Contactar con el soporte técnico](#support) al final de este artículo para ver los pasos siguientes.

## La base de datos de origen tiene MÁS filas que el BI del Magento {#morerows}

Si la base de datos de origen tiene más filas que el BI de Magento y el espacio es mayor que el número de pedidos que puede esperar recibir durante la duración de un ciclo de actualización, puede haber un problema de conexión. Esto significa que Magento BI no puede extraer nuevos datos de la base de datos de origen, lo que puede ocurrir por varios motivos.

Vaya a la página Conexiones y observe el estado del origen de datos que contiene la tabla `order`:

1. **Si el estado es Re-auth** , la conexión no está usando las credenciales correctas. Haga clic en la conexión, introduzca las credenciales correctas y vuelva a intentarlo.
1. **Si el estado es Error** , es posible que la conexión no se haya configurado correctamente en el servidor. Las conexiones fallidas normalmente se deben a un nombre de host incorrecto o a que el servidor de destino no acepta conexiones en el puerto especificado. Haga clic en la conexión y vuelva a comprobar la ortografía del nombre de host y que se ha introducido el puerto correcto. En el lado del servidor, asegúrese de que el puerto pueda aceptar conexiones y de que el cortafuegos tenga la dirección IP del BI del Magento (54.88.76.97/32) permitida. **Si la conexión continúa fallando** , consulte la [sección Contacto con soporte técnico](#support) al final de este artículo para ver los pasos siguientes.
1. **Si el estado es Correcto** , la conexión no es el problema y la compatibilidad con RJ necesita involucrarse. Consulte [Contactar con el soporte técnico](#support) al final de este artículo para ver los pasos siguientes.

## La base de datos de origen tiene MENOS filas que Magento BI {#lessrows}

Si la base de datos de origen tiene menos filas que el BI de Magento, es posible que las filas se eliminen de la base de datos de origen y el BI de Magento no recoja estas eliminaciones. ** [Eliminar datos](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html) puede provocar discrepancias, tiempos de actualización más largos y una serie de dolores de cabeza logísticos** , por lo que recomendamos encarecidamente que no elimine datos a menos que sea realmente necesario.

Sin embargo, si se eliminan filas de la tabla, observe la frecuencia de comprobación de la clave principal. Volver a comprobar la clave principal significa que se comprobará si la tabla contiene filas eliminadas.

En el Administrador de Datas Warehouse, las columnas de clave principal se marcan con un símbolo de clave. En nuestro ejemplo, la clave principal es la columna **order\_id**:

![](assets/Export_Discrepancies_3.png)

Si la clave principal ya está configurada para volver a comprobarse o las filas nunca se eliminan de esta tabla, necesitará la asistencia técnica de RJ para identificar el problema. Consulte la siguiente sección para ver los pasos siguientes.

## Contacto con el soporte {#support}

Si no es capaz de identificar el origen del problema, necesitará realizar un bucle en el soporte de RJ. Antes de enviar un ticket, haga lo siguiente:

* **Si la base de datos de origen y el BI de Magento tienen el mismo número de filas** y las frecuencias de comprobación se han configurado correctamente, realice una búsqueda en la hoja de cálculo **para encontrar qué valores order\_id tienen un valor order\_total diferente entre el BI de Magento y la base de datos de origen.** Incluya estos valores cuando envíe su solicitud.
* **Si la base de datos de origen tiene MÁS filas que el Magento BI** y la conexión se muestra como Correcta o continúa fallando, necesitaremos saber el nombre de la conexión y el mensaje de error que está viendo, si hay alguno.
* **Si la base de datos de origen tiene MENOS filas que el BI de Magento,** filas no se eliminan de la tabla y las frecuencias de comprobación se han establecido correctamente, realice una búsqueda VLOOKUP en la hoja de cálculo **para encontrar qué valores order\_id están en el BI de Magento**, pero no en la base de datos de origen. Incluya estos valores cuando envíe su solicitud.

## Lectura relacionada

* [Lista de comprobación de diagnóstico de discrepancias de datos](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy)
* [Políticas de servicio de Adobe Commerce Intelligence](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies)
* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce

