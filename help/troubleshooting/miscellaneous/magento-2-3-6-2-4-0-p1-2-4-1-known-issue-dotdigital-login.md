---
title: "Problema conocido de Adobe Commerce 2.3.6, 2.4.0-p1, 2.4.1: inicio de sesión dotdigital"
description: Este artículo describe un problema conocido de Adobe Commerce 2.3.6, 2.4.0-p1 y 2.4.1 en el que es imposible iniciar sesión en [dotdigital](https://dotdigital.com/) mediante el Panel de administración cuando la cuenta dotdigital está habilitada.
exl-id: 427d895c-8c03-4ced-813a-eeaa67f1d1f0
feature: Configuration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Problema conocido de Adobe Commerce 2.3.6, 2.4.0-p1, 2.4.1: inicio de sesión dotdigital

Este artículo describe un problema conocido de Adobe Commerce 2.3.6, 2.4.0-p1 y 2.4.1 en el que es imposible iniciar sesión en [dotdigital](https://dotdigital.com/) mediante el Panel de administración cuando la cuenta dotdigital esté habilitada.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube y Adobe Commerce local 2.3.6 (solo explorador Safari)
* Adobe Commerce en la infraestructura en la nube y Adobe Commerce local 2.4.0-p1 (solo explorador Safari)
* Adobe Commerce en la infraestructura en la nube y Adobe Commerce local 2.4.1 (solo explorador Safari)

## Problema

<u>Requisitos previos</u>:

1. existe una cuenta dotdigital.
1. Existen credenciales válidas de la API dotdigital en Adobe Commerce.

<u>Pasos a seguir</u>:

1. Ir a **Tiendas** > **Configuración** > **DOTDIGITAL** > **Configuración de chat** > **Habilitado** se establece en *Sí.*
1. Haga clic en **Configurar** in **Configurar el widget de chat** o **Configuración de equipos de chat**.

<u>Resultados esperados</u>:

La página de configuración de chat se debe abrir correctamente a través del Panel de administración.

<u>Resultados reales</u>:

No se puede iniciar sesión en dotdigital.

## Solución

Solución alternativa: utilice un explorador alternativo a Safari para esta situación concreta.

## Lectura relacionada

[Problema conocido de Adobe Commerce 2.4.1: la dirección de vértice no se valida con diferentes direcciones de envío/facturación](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md) en nuestra base de conocimiento de soporte.
