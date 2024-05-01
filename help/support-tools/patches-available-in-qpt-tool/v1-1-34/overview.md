---
title: 'Información general: [!DNL Quality Patches Tool] (QPT) v1.1.34'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.34.
feature: Tools and External Services
role: Admin
exl-id: 79998832-26cb-4c11-a505-08c3382f86d4
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.34

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.34.

QPT v1.1.34 incluye los siguientes parches:

1. **ACSD-52277**: corrige un problema en el cual un usuario administrador no se redirige correctamente después de seleccionar la vista de la tienda al crear un nuevo pedido en el administrador.
1. **ACSD-50813**: corrige un problema en el cual un administrador no puede agregar productos agrupados que contengan una barra oblicua en el SKU con [!UICONTROL Add Products by SKU] al orden de administración.
1. **ACSD-51630**: corrige un problema en el que una gran cantidad de mensajes del sistema ralentiza la descarga de páginas de administración.
1. **ACSD-51853**: corrige el problema en el cual los estilos de texto copiados no se aplican al utilizar [!DNL Page Builder].
1. **ACSD-52160**: corrige un problema en el cual un resultado de validación de producto contra la regla de precio del carro de compras no se evaluaba correctamente, según la condición de regla *Si se ENCUENTRA/NO SE ENCUENTRA un artículo en el carro de compras con todas/cualquiera de estas condiciones en true*.
1. **ACSD-51636**: corrige un problema en el cual un administrador no puede agregar nuevos usuarios desde la sección de cuenta de cliente a pesar de tener todas las funciones y permisos necesarios.
1. **ACSD-51739**: corrige el problema en el que se devuelve un error cuando el `structure_id` se solicita en un `CompanyTeam` petición GraphQL.
1. **ACSD-51857**: corrige el problema en el que un rendimiento lento de `aggregate_sales_report_bestsellers_data` el informe cron afecta a los archivos grandes `sales_order` y `sales_order_item` tablas de base de datos.
1. **ACSD-48448**: corrige el problema en el que se produce un problema de condición de carrera durante las cancelaciones de pedidos, que provoca la entrada duplicada en *inventory_reservation* tabla.
1. **ACSD-52689**: corrige el problema en el que las imágenes no se pueden cargar en [!DNL Amazon S3] mediante la API de REST.

Utilice el menú de la izquierda para navegar a una página específica del parche.
