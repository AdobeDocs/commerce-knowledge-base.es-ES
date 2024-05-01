---
title: 'Información general: [!DNL Quality Patches Tool] (QPT) v1.0.20'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.0.20.
exl-id: 13ed85f9-4ecb-467f-9ed0-ceec4ac200db
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] Información general de (QPT) v1.0.20

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.0.20.

QPT v1.0.20 incluye los siguientes parches:

1. **MC-41359**: corrige el problema de la configuración incorrecta de los parámetros de cookie de SameSite.
1. **MDVA-11189**: corrige el problema que se producía cuando, después de importar un archivo CSV para actualizar las existencias del producto, las filas del `cataloginventory_stock` se eliminan.
1. **MDVA-15546**: corrige el problema en el que después de crear una solicitud de *Columna entity_id donde la cláusula es ambigua* el error aparece en el registro de excepciones.
1. **MDVA-19640**: soluciona el problema donde [!DNL Advanced Reporting] no muestra ningún dato.
1. **MDVA-21095**: corrige el problema que se producía al crear una consulta `INSERT INTO search_tmp` no finalizará después de actualizar el valor de atributo masivo.
1. **MDVA-22026**: corrige el problema en el que falla la importación de productos desde un archivo CSV, incluidas imágenes de direcciones URL externas.
1. **MDVA-22383**: soluciona el problema que causaba que tardara mucho tiempo en guardar un producto y que se produjeran saltos de página.
1. **MDVA-23845**: corrige el problema en el cual las plantillas de correo electrónico no se pueden previsualizar después de habilitar la minificación de JavaScript.
1. **MDVA-26639**: corrige el problema en el cual si se crea una nueva plantilla de correo electrónico de confirmación de pedido, los elementos del pedido no aparecen en el correo electrónico.
1. **MDVA-33168**: corrige el problema que se producía al actualizar un atributo de producto mediante API y todos los demás atributos cambian a un valor vacío.
1. **MDVA-36170**: Esto corrige el problema en el que la consulta de GraphQL no se almacena en caché mediante la etiqueta de caché de categoría.

Utilice el menú de la izquierda para navegar a una página específica del parche.
