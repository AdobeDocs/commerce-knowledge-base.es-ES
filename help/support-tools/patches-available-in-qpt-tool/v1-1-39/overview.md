---
title: 'Información general: [!DNL Quality Patches Tool] (QPT) v1.1.39'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.39.
feature: Tools and External Services
role: Admin, Developer
exl-id: 48563701-0fa0-4c88-943e-78b421b806b5
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.39

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.39.

QPT v1.1.39 incluye los siguientes parches:

1. **ACSD-53704**: corrige el problema en el que el historial de saldo de puntos de recompensa se calcula de forma incorrecta tras la caducidad de los puntos de recompensa.
1. **ACSD-53583**: mejora el rendimiento de reindexación parcial para *Productos de categoría* y *Categorías de productos* indexadores.
1. **ACSD-54026**: corrige un mensaje de error incorrecto para un `updateCompanyRole` Solicitud de GraphQL para un usuario no autorizado.
1. **ACSD-54106**: corrige el problema en el cual la ordenación de productos de categoría por nombre para caracteres acentuados turcos es incorrecta.
1. **ACSD-52219**: corrige el problema en el cual las cuadrículas de administración guardadas de filtros no funcionan como se espera cuando se cambia con frecuencia entre vistas de marcadores.
1. **ACSD-54342**: corrige un mensaje de error incorrecto *Error en la estructura de datos: los valores están mezclados* al importar un archivo CSV sin datos válidos.
1. **ACSD-54660**: Se ha añadido un nuevo atributo de entrada *sort* para ordenar los pedidos de los clientes en GraphQL por `sort_field` y `sort_direction`.
1. **ACSD-54776**: corrige el problema donde no está marcado *[!UICONTROL Use Default Value]* y los valores de campo de producto no predeterminados no se guardan para la segunda vista del sitio web, la tienda y la tienda.
1. **ACSD-53998**: corrige el problema en el que un **[!UICONTROL Dynamic Block]** basado en un **[!UICONTROL Customer Segment]** no funciona correctamente después de cerrar sesión en una cuenta de cliente.
1. **ACSD-53204**: correcciones *No se puede guardar el producto.* error al realizar solicitudes simultáneas para añadir imágenes a la galería de productos utilizando `rest/V1/products/<sku>/media` punto final.
1. **ACSD-47657**: Se ha agregado un mecanismo de almacenamiento en caché para las credenciales de AWS. Un proveedor de credenciales ahora utiliza la caché de Magento para almacenar en caché las credenciales recuperadas de AWS para la configuración EC2.

Utilice el menú de la izquierda para navegar a una página específica del parche.
