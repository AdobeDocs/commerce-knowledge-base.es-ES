---
title: 'Adobe Commerce 2.4.2 B2B: la plantilla de correo electrónico no actualiza el correo electrónico'
description: Este artículo describe un problema conocido de Adobe Commerce 2.4.2 B2B en el que la actualización de parte de la información de una plantilla de correo electrónico no se actualiza en los correos electrónicos. Este problema afecta al contenido del correo electrónico, como la información del cliente, las tasas de cambio, el símbolo de moneda, el cambio de plantilla de correo electrónico, etc. No hay una solución disponible en este momento, pero hay una solución al final de este artículo.
exl-id: 31b7086f-a941-4682-aa07-301ac31d543b
feature: B2B, Communications
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bb03f6c4-cab9-560e-9d02-5816e1808d17
    internal-label: Communications
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%
---
# Adobe Commerce 2.4.2 B2B: la plantilla de correo electrónico no actualiza el correo electrónico

Este artículo describe un problema conocido de Adobe Commerce 2.4.2 B2B en el que la actualización de parte de la información de una plantilla de correo electrónico no se actualiza en los correos electrónicos. Este problema afecta al contenido del correo electrónico, como la información del cliente, las tasas de cambio, el símbolo de moneda, el cambio de plantilla de correo electrónico, etc. No hay una solución disponible en este momento, pero hay una solución al final de este artículo.

## Productos y versiones afectados

* Adobe Commerce local 2.4.2
* Adobe Commerce cloud Infrastructure 2.4.2
* B2B 1.3.1

## Problema

<u>Pasos a seguir</u>:

1. El administrador de la empresa crea un pedido de compra en el front-end.
1. Consulte el correo electrónico de aprobación automática. **nombre de cliente** / **tasa de cambio** deben ser valores esperados.
1. Cambie el símbolo de moneda (**Tiendas > Configuración > Configuración de moneda > Opciones de moneda**) en el nombre del administrador y del administrador de la empresa en la página Cuenta de cliente.
1. El administrador de clientes crea otro pedido de compra en el administrador.
1. Consulte el correo electrónico de aprobación automática.

<u>Resultados esperados:</u>

El nombre del cliente y el símbolo de moneda se cambian en los correos electrónicos y sus nuevos valores son los esperados.

<u>Resultados reales</u>:

El nombre del cliente y el símbolo de moneda no se cambian en los correos electrónicos y tienen sus valores anteriores.

## Solución

Ejecute manualmente el trabajo cron o el consumidor para propagar la nueva información.

## Lectura relacionada

* [Administrar colas de mensajes](https://experienceleague.adobe.com/es/docs/commerce-operations/configuration-guide/message-queues/manage-message-queues) en nuestra documentación para desarrolladores.
