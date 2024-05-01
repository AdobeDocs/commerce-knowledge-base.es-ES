---
title: Complemento Composer contra ataques de confusión de dependencias
description: Este artículo proporciona información sobre el complemento del compositor lanzado para los ataques de confusión de dependencias y recomendaciones para evitar el error. El complemento Composer se introdujo junto con la versión 2.4.3 de Adobe Commerce para proteger a los comerciantes de Adobe Commerce de los ataques de confusión de dependencias.
exl-id: 42543043-cf60-4431-80e9-866771c5c87b
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# Complemento Composer contra ataques de confusión de dependencias

Este artículo proporciona información sobre el complemento del compositor lanzado para los ataques de confusión de dependencias y recomendaciones para evitar el error. El complemento Composer se introdujo junto con la versión 2.4.3 de Adobe Commerce para proteger a los comerciantes de Adobe Commerce de los ataques de confusión de dependencias.

## Productos y versiones afectados

* Adobe Commerce 2.4.3 y versiones futuras (todos los métodos de implementación)

## Problema

Se detecta un caso potencial de ataque de confusión de dependencia activo a través de al menos una de las dependencias directas o indirectas definidas en `composer.json` por el complemento compositor `magento/composer-dependency-version-audit-plugin` durante la instalación/actualización del compositor.

<u>Pasos a seguir</u>:

Al instalar/actualizar Composer, el complemento de Composer detendrá el proceso si detecta un posible ataque de confusión de dependencias. En ese caso, la instalación/actualización del compositor fallará con un mensaje de error similar al siguiente:

*```Higher matching version x.x.x of package/name was found in public repository packagist.org than x.x.x in private.repo. Public package might've been taken over by a malicious entity; please investigate and update package requirement to match the version from the private repository.```*

## Causa

El ataque de confusión de dependencias permite ejecutar código arbitrario de forma remota en un servidor al engañar a un administrador de dependencias (por ejemplo, PHP&#39;s Composer) para que descargue un paquete malicioso de una fuente pública en lugar del paquete original de un repositorio privado.

Un ataque de este tipo puede incluso pasar desapercibido si un atacante es capaz de mantener la funcionalidad del paquete original.

Los atacantes pueden aprovechar esta vulnerabilidad si un paquete solo está disponible a través de repositorios privados, pero no está registrado en el público. A continuación, el atacante carga un paquete con el mismo nombre en el repositorio público y le proporciona una versión superior a la disponible de forma privada. El administrador de dependencias comparará las versiones de los paquetes disponibles tanto de forma privada como pública y elegirá la más alta del repositorio público. El código malintencionado descargado por el administrador de dependencias se ejecutará con los mismos privilegios que el código de la aplicación.

## Solución

### Recommendations a comerciantes

* Tome en serio el mensaje de error que se muestra cuando el complemento detiene la instalación o actualización del compositor y póngase en contacto con el desarrollador de la extensión si reconoce el paquete potencialmente comprometido.
* Puede instalar Adobe Commerce con la versión segura del paquete desde Marketplace u otro repositorio privado de confianza.
* Cambie la versión del paquete necesaria en composer.json a la versión exacta que se encuentra en Marketplace para continuar con la instalación/actualización del compositor.

### Expectativas de los desarrolladores de extensiones

* No hay forma de saber con certeza si el paquete de un complemento, si de un repositorio público, se ha visto comprometido o no. El complemento detectará cuándo una versión pública de un paquete en packagist.org tiene una versión superior a la disponible en un repositorio privado como [repo.magento.com](https://repo.magento.com). Recomendamos encarecidamente que los desarrolladores de extensiones eviten estas situaciones y no publiquen versiones más recientes públicamente que las disponibles a través de [repo.magento.com](https://repo.magento.com).
* Adobe Commerce entiende que el proceso de revisión del mercado puede retrasar la disponibilidad de la versión de las extensiones, pero el proceso está ahí para mantener a los comerciantes seguros y para ayudar a los desarrolladores de extensiones a encontrar errores accidentales que podrían haberse perdido.
