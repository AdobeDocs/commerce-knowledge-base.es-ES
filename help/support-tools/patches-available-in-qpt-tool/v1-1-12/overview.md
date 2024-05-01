---
title: 'Información general: [!DNL Quality Patches Tool] (QPT) v1.1.12'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.12.
exl-id: 749dbfd5-9ded-4919-8c57-0f66c85751e9
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] Información general de (QPT) v1.1.12

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.12.

QPT v1.1.12 incluye los siguientes parches:

1. **MDVA-39546**: corrige un problema en el cual la fecha de inicio de la actualización de ensayo se podía establecer en una fecha anterior a la fecha actual durante la edición.
1. **MDVA-39713**: corrige el problema en el que el usuario puede editar la hora de inicio de una actualización programada activa.
1. **MDVA-39993**: corrige el problema en el cual los cambios de inventario realizados a través de la API no se reflejan en la página del producto en el front-end.
1. **MDVA-41136**: corrige el problema en el que la fecha de caducidad del `mage-cache-sessid` no se amplía, lo que provoca la limpieza de datos del cliente.
1. **MDVA-41229**: corrige el problema en el cual las imágenes disponibles en el back-end no se muestran en el front-end después de la importación de productos configurables.
1. **MDVA-41628**: corrige el problema en el cual los usuarios administradores restringidos existentes obtienen acceso a los nuevos recursos cuando se agregan nuevos módulos.
1. **MDVA-42410**: corrige el problema en el cual los informes de cupones solo muestran la moneda base predeterminada.
1. **MDVA-42645**: corrige un problema en el que el administrador no puede devolver puntos de recompensa si la funcionalidad de crédito de tienda está deshabilitada.
1. **MDVA-42689**: corrige el problema en el que Adobe Commerce emite un *Infracción de restricción de integridad* error al actualizar las categorías de productos durante la importación.
1. **MDVA-42855**: corrige el problema en el cual una nueva dirección de cliente no se guarda en la libreta de direcciones durante el cierre de compra.
1. **MDVA-42950**: corrige el problema de que los vídeos no se reproduzcan en la página del producto.
1. **MDVA-43232**: corrige el problema que causaba que se ordenaran productos en [!DNL Visual Merchandiser] por Precio especial inferior/superior causa un error al guardar la categoría.
1. **MDVA-43348**: corrige el problema en el cual la solicitud GraphQL de tarjeta de regalo muestra un error si `gift_card_options` contain *uid*.
1. **MDVA-43414**: corrige el error grave de PHP que se produce al ejecutar el `inventory.reservations.updateSalabilityStatus` poner en cola al consumidor con SKU numéricas.
1. **MDVA-43726**: corrige el problema en el que la regla de precio de catálogo basada en la coincidencia de atributos en el nivel de almacén no se aplica después de una reindexación parcial.
1. **MDVA-43731**: soluciona el problema donde *Buscar sinónimos* ya no funciona cuando se agrega un valor en *Términos mínimos que deben cumplirse*.

Utilice el menú de la izquierda para navegar a una página específica del parche.
