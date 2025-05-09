---
title: "MDVA-42046: Valor incorrecto asignado para el atributo del producto"
description: El parche MDVA-42046 corrige el problema en el que se asigna un valor incorrecto para el atributo del producto al actualizar un producto que tiene un campo de entrada de fecha. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. El ID del parche es MDVA-42046. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: 837f5582-849c-43a3-ae02-87f71fb96061
feature: Attributes, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# MDVA-42046: Valor incorrecto asignado para el atributo del producto

El parche MDVA-42046 corrige el problema en el que se asigna un valor incorrecto para el atributo del producto al actualizar un producto que tiene un campo de entrada de fecha. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. El ID del parche es MDVA-42046. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.4 - 2.3.5-p2 y 2.4.0 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Después de guardar un producto con `news_from_date` y/o `news_to_date` campos, los valores de esos campos se restablecen a los valores predeterminados.

<u>Pasos a seguir</u>:

1. Cree un producto sencillo.
1. Exporte el producto creado en el paso uno.
1. En el archivo CSV exportado, coloque algunos valores en los campos `news_from_date` y `news_to_date`. Por ejemplo, 15 de mayo de 2021 y 18 de junio de 2021.
1. Importe el producto utilizando el archivo CSV modificado.
1. Añada a la cuadrícula de productos las columnas adicionales &quot;Definir producto como nuevo desde la fecha&quot; y &quot;Definir producto como nuevo desde la fecha&quot;.
1. Abra la página de edición del producto y, sin realizar ningún cambio, haga clic en **Guardar**.
1. Vuelva a la cuadrícula del producto y compruebe los datos del producto.

<u>Resultados esperados</u>:

Tanto &quot;Establecer producto como nuevo desde la fecha&quot; como &quot;Establecer producto como nuevo hasta la fecha&quot; son los mismos que antes de guardar.

<u>Resultados reales</u>:

* Los valores de las columnas &quot;Establecer producto como nuevo desde la fecha&quot; y &quot;Establecer producto como nuevo hasta la fecha&quot; cambian.

* La columna &quot;Establecer producto como nuevo desde la fecha&quot; muestra la fecha actual y la columna &quot;Establecer producto como nuevo desde la fecha&quot; está vacía.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/usage) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en nuestra documentación para desarrolladores.
