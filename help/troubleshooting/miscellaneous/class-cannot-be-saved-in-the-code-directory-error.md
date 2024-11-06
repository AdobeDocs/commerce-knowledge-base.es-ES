---
title: '"Error "La clase no se puede guardar en el directorio de códigos"'
description: Este artículo describe cómo solucionar el problema en el que la forma en que especificó las dependencias impide que las clases se generen automáticamente sobre la marcha y se obtiene el mensaje de error *"Class cannot be saved in the generated/code directory"*.
exl-id: e2c00d4d-31c3-4446-a317-a8ac92c707d5
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# Error &quot;La clase no se puede guardar en el directorio de códigos&quot;

Este artículo describe cómo solucionar el problema en el que la forma en que especificó las dependencias impide que las clases se generen automáticamente sobre la marcha y se obtiene el mensaje de error *&quot;La clase no se puede guardar en el directorio generated/code&quot;*.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube 2.2.0 o posterior

## Problema

<u>Pasos a seguir</u>

1. En su entorno local, escriba una clase personalizada con una dependencia en la clase generada automáticamente.
1. Ejecute el escenario en el que se activa la clase personalizada y vea que funciona correctamente.
1. Confirme e inserte sus cambios en el entorno de integración. Esto almacenaría en déclencheur el proceso de implementación. La implementación es correcta.
1. En el [entorno de integración](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md), ejecute el escenario donde se activará la clase personalizada.

<u>Resultado esperado</u>

Todo funciona correctamente, del mismo modo que en su entorno local.

<u>Resultado real</u>

Error con el mensaje de error que indica que la clase no se puede guardar en el directorio `generated/code`.

## Causa

La causa del problema es que la clase de la que depende no se genera durante la implementación y no se puede generar más adelante cuando se activa la clase, ya que el directorio `generated/code` no está disponible para escribir una vez completada la implementación.

Esto puede deberse a dos razones principales:

* Caso 1: La clase con dependencias en clases generadas automáticamente se encuentra en el punto de entrada (como `index.php` ), que no se analiza para detectar dependencias durante la implementación.
* Caso 2: La dependencia de la clase generada automáticamente se especifica directamente (compárela con el uso recomendado del constructor para declarar la dependencia).

## Solución

Una solución común para ambos casos sería crear una fábrica real en lugar de la clase generada automáticamente.

O hay una solución particular para cada caso.

### Caso 1 solución específica

Mueva el código de clase desde el punto de entrada a un módulo independiente y, a continuación, utilícelo en el punto de entrada.

<u>Ejemplo</u>

Código original en, por ejemplo, `index2.php` :

```php
<?php
use YourVendor\SomeModule\Model\GeneratedFactory;

require realpath(__DIR__) . '/../app/bootstrap.php';
$bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);

class SomeClass
{
    private $generatedFactory;

    public function __construct(GeneratedFactory $generatedFactory)
    {
        $this->generatedFactory = $generatedFactory;
    }

// Some code here...
}

$someObject = $bootstrap->getObjectManager()->create(SomeClass::class);

// There is some code that uses $someObject
```

Debe seguir estos pasos:

1. Mover la definición de clase a `app/code/YourVendor/YourModule`:

   ```php
      <?php
       namespace YourVendor\YourModule;
       use YourVendor\YourModule\Model\GeneratedFactory;
       class YourClass
       {
           private $generatedFactory;
   
           public function __construct(GeneratedFactory $generatedFactory)
           {
               $this->generatedFactory = $generatedFactory;
           }
       // Some code here...
       }
   ```

1. Edite el punto de entrada `my_api/index.php` para que tenga el siguiente aspecto:

   ```php
     <?php
     use YourVendor\YourModule\YourClass;
         require realpath(__DIR__) . '/../app/bootstrap.php';
         $bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
         $someObject = $bootstrap->getObjectManager()->create(YourClass::class);
     // Some code using $someObject
   ```

### Caso 2 solución específica

Mueva la declaración de dependencia al constructor.

<u>Ejemplo</u>

Declaración de clase original:

```php
<?php
namespace YourVendor\YourModule;

use YourVendor\SomeModule\Model\GeneratedFactory;
use Magento\Framework\App\ObjectManager;

class YourClass
{
    private $generatedFactory;
    private $someParam;

    public function __construct($someParam)
    {
        $this--->someParam = $someParam;
        $this->generatedFactory = ObjectManager::getInstance()->get(GeneratedFactory::class);
    }

    // Some code here...
}
```

Debe cambiar su constructor de la siguiente manera:

```php
<?php
namespace YourVendor\YourModule;

use YourVendor\YourModule\Model\GeneratedFactory;
use Magento\Framework\App\ObjectManager;

class YourClass
{
    private $generatedFactory;
    private $someParam;

    public function __construct($someParam, GeneratedFactory $generatedFactory = null)
    {
        $this->someParam = $someParam;
        $this->generatedFactory = $generatedFactory ?: ObjectManager::getInstance()->get(GeneratedFactory::class);
    }

    // Some code here...
}
```

## Lectura relacionada

* [Generación de código](https://developer.adobe.com/commerce/php/development/components/code-generation/) en nuestra documentación para desarrolladores.
