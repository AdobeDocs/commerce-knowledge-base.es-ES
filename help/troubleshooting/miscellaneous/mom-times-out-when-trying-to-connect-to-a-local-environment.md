---
title: El sistema Magento Order Management (OMS) para Adobe Commerce agota el tiempo de espera
description: Este artículo proporciona una solución para el problema en el que el sistema Magento Order Management (OMS) para Adobe Commerce no puede registrar el microservicio instalado localmente con MOM mediante ngrok, porque MOM agota el tiempo de espera al intentar la devolución de llamada.
exl-id: 19149d8c-ea24-46fb-8815-9f637afe46ca
feature: System
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# El sistema Magento Order Management (OMS) para Adobe Commerce agota el tiempo de espera

Este artículo proporciona una solución para el problema en el que el sistema Magento Order Management (OMS) para Adobe Commerce no puede registrar el microservicio instalado localmente con MOM mediante ngrok, porque MOM agota el tiempo de espera al intentar la devolución de llamada.

## Productos y versiones afectados

* Adobe Commerce 2.3.1
* OMS
* ngrok

>[!WARNING]
>
>Descargo de responsabilidad: Adobe Commerce no recomienda ni respalda ninguna herramienta en particular para establecer túneles. Los anteriores son solo sugerencias. Para obtener más información, consulte la [documentación de ngrok](https://ngrok.com/docs).

## Problema

<u>Pasos a seguir</u>

1. Instale Adobe Commerce en su entorno local.
1. Configure ngrok para crear un túnel que exponga el servidor local.
1. Probar [conectar con OMS](https://omsdocs.magento.com/en/integration/connector/setup-tutorial/).

<u>Resultado esperado</u>

Conexión establecida correctamente.

<u>Resultado real</u>

MCOM parece agotar el tiempo de espera al intentar devolver la llamada a la URL de ngrok.

## Causa

Una de las posibles razones del tiempo de espera es que los servidores están ubicados geográficamente demasiado lejos y la conexión tarda demasiado.

## Solución

Añada un parámetro que especifique la región al iniciar ngrok. Como el siguiente:

```bash
./ngrok http 80 -region eu
```

La región predeterminada es EE. UU. Consulte [todos los valores posibles](https://ngrok.com/docs#config_region).
