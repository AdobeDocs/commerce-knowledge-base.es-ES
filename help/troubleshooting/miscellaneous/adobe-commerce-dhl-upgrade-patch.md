---
title: Aplicar un parche para seguir ofreciendo DHL como transportista
description: Este artículo proporciona un parche que permite a los comerciantes que utilizan Adobe Commerce 2.4.4 y versiones anteriores seguir ofreciendo el envío DHL, después de que el esquema DHL 6.0 quede obsoleto entre finales de julio y septiembre de 2022.
exl-id: 4350e83a-495b-41b4-a526-dae5923e9d41
feature: Orders, Shipping/Delivery, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Aplicar un parche para seguir ofreciendo DHL como transportista


## Productos y versiones afectados

* Adobe Commerce 2.4.4 y anteriores, todos los métodos de implementación.

## Problema

DHL presenta una versión de esquema 6.2 y la versión 6.0 quedará obsoleta entre finales de julio y septiembre de 2022. La integración de Adobe Commerce 2.4.4 y versiones anteriores de DHL solo admite la versión 6.0.

## Solución

Adobe Commerce 2.4.5, cuyo lanzamiento está programado para agosto de 2022, contendrá la integración actualizada con DHL mediante el esquema de la versión 6.2. Hasta que se publique la nueva versión (o en caso de que decida no actualizarla), le recomendamos que aplique el parche AC-3022, implementando la compatibilidad con el esquema DHL versión 6.2, para seguir ofreciendo envíos de DHL en su tienda después de la desuso.

## Parche

El ID de parche es AC-3022 disponible en la versión 1.1.16 de la herramienta de parches de calidad.
Consulte el artículo [Herramienta de parches de calidad (QPT) > Uso](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/usage) en nuestra documentación para desarrolladores para obtener información sobre cómo usar QPT e instalar parches.

El parche se aplica a las siguientes versiones de Adobe Commerce:

* 2.4.0 - 2.4.4-p1
* 2.3.7

## Lectura relacionada

* [Transportistas de envío > DHL](https://experienceleague.adobe.com/es/docs/commerce-admin/stores-sales/delivery/shipping-carriers/dhl) en nuestra guía de usuario
* [Métodos de envío](https://experienceleague.adobe.com/es/docs/commerce-admin/config/sales/delivery-methods) en nuestra guía de usuario
