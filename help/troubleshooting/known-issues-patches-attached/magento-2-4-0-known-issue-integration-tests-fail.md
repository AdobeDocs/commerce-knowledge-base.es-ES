---
title: "Problema conocido de Adobe Commerce 2.4.0: las pruebas de integración fallan"
description: Este artículo proporciona un parche para el problema de Adobe Commerce 2.4.0 en el que las pruebas de integración fallan porque la declaración de Dotdigitalgroup\Email\Test\Integration\Model\Sync\Importer\ImporterFailedTest::setUp() no es compatible con PHPUnit 9, que se usa para 2.4.0.
exl-id: 8e0ca2da-81d9-4561-a009-593240f46e41
feature: Integration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Problema conocido de Adobe Commerce 2.4.0: las pruebas de integración fallan

Este artículo proporciona un parche para el problema de Adobe Commerce 2.4.0 donde las pruebas de integración fallan porque la declaración de `Dotdigitalgroup\Email\Test\Integration\Model\Sync\Importer\ImporterFailedTest::setUp()` no es compatible con PHPUnit 9 que se usa para 2.4.0.

## Productos y versiones afectados

* Adobe Commerce en infraestructura en la nube 2.4.0
* Adobe Commerce local 2.4.0

## Problema

<u>Pasos a seguir</u>

Ejecute pruebas de integración 2.4.0.

<u>Resultado esperado</u>

Las pruebas se superan.

<u>Resultado real</u>

*Error grave de PHP: La declaración de Dotdigitalgroup\\Email\\Test\\Integration\\Model\\Sync\\Importer\\ImporterFailedTest::setUp() debe ser compatible con PHPUnit\\Framework\\TestCase::setUp(): void en /var/www/vendor/dotmailer/dotmailer-magento2-extension/Test/Integration/Model/Sync/Importer/ImporterFailedTest.php en la línea 36*

## Solución

Aplique el parche proporcionado en este artículo.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[BUNDLE-2684-composer.patch](assets/BUNDLE-2684-composer.patch.zip)

### Versiones de Adobe Commerce compatibles:

El parche se ha creado para:

* Adobe Commerce en infraestructura en la nube 2.4.0
* Adobe Commerce local 2.4.0

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de soporte técnico para obtener instrucciones detalladas.

## Archivos adjuntos
