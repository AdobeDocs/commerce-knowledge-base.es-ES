---
title: "Información general:  [!DNL Quality Patches Tool] (QPT) v1.0.5"
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.0.5.
exl-id: 439358e8-d6bc-4d35-aee1-f4fc33ae267c
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Información general de [!DNL Quality Patches Tool] (QPT) v1.0.5

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.0.5.

QPT v1.0.5 incluye los siguientes parches:

1. **MDVA-28191**: corrige el problema en el cual no se cargan métodos de pago durante la creación del pedido a través del administrador.
1. **MDVA-28409**: corrige el problema en el que el trabajo cron de `sales_clean_quotes` falla con el error *falta de memoria* cuando el número de comillas caducadas en la base de datos es enorme.
1. **MDVA-28661**: corrige el problema por el que se genera un error en la sección de cuenta de compañía de los usuarios de la compañía después de cambiar el administrador de la compañía.
1. **MDVA-28763**: corrige el problema en el cual la imagen del producto se duplica después de actualizar la información del producto mediante la API de REST más de una vez.
1. **MDVA-29042**: corrige el problema por el cual los permisos del catálogo se cambiaban a *Permitir* automáticamente después de que se agregara un nuevo producto al catálogo compartido.
1. **MDVA-29959**: corrige el problema en el cual un usuario administrador restringido con permisos de *Compañías* no tiene permiso para eliminar una cuenta de compañía.
1. **MDVA-30107**: corrige el problema por el que el conmutador de tiendas no funciona como se esperaba si se usan direcciones URL base diferentes para las vistas de tiendas.
1. **MDVA-30265**: corrige el problema por el que el vínculo de seguimiento de envíos deja de funcionar después de la creación de la factura.
1. **MDVA-30284**: corrige el problema en el que el indizador de búsqueda en el catálogo falla debido al siguiente error de *[!DNL Elasticsearch]: se ha superado el límite del total de campos en el índice.*
1. **MDVA-30428**: corrige el problema en el cual los clientes no pueden agregar un producto a la lista de deseos si este producto está asignado a un origen de inventario personalizado.
1. **MDVA-30593**: corrige el problema en el cual las ofertas que caducaron según la configuración de Duración de la oferta no se limpian.

Utilice el menú de la izquierda para navegar a una página específica del parche.
