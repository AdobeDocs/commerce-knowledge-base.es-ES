---
title: Cómo añadir un nuevo país a Adobe Commerce
description: En este artículo se explica cómo agregar un país que no esté presente en Adobe Commerce ni en la biblioteca de configuración regional de Zend. Esto requiere cambios en el código y la base de datos que constituyen personalizaciones del cliente según los términos del acuerdo aplicables. Tenga en cuenta que los materiales de ejemplo incluidos en este artículo se proporcionan "TAL CUAL" sin garantía de ningún tipo. Ni el Adobe ni ninguna otra entidad afiliada están obligados a mantener, corregir, actualizar, cambiar, modificar o apoyar estos materiales. Aquí describiremos los principios básicos de lo que se debe hacer para lograr esto.
exl-id: af499add-4966-4a3a-972a-62a34c169a1b
feature: Build, Cache
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '1105'
ht-degree: 0%

---

# Cómo añadir un nuevo país a Adobe Commerce

En este artículo se explica cómo agregar un país que no esté presente en Adobe Commerce ni en la biblioteca de configuración regional de Zend. Esto requiere cambios en el código y la base de datos que constituyen personalizaciones del cliente según los términos del acuerdo aplicables. Tenga en cuenta que los materiales de ejemplo incluidos en este artículo se proporcionan &quot;TAL CUAL&quot; sin garantía de ningún tipo. Ni el Adobe ni ninguna otra entidad afiliada están obligados a mantener, corregir, actualizar, cambiar, modificar o apoyar estos materiales. Aquí describiremos los principios básicos de lo que se debe hacer para lograr esto.

En este ejemplo, creamos un nuevo módulo de Adobe Commerce con un parche de datos que se aplica durante el proceso de instalación o actualización de Adobe Commerce, y añadimos un País abstracto con el código de país XX a Adobe Commerce. El [Directorio de Adobe Commerce](https://developer.adobe.com/commerce/php/module-reference/module-directory/) crea una lista inicial de países y, a continuación, utiliza Parches de configuración para anexar territorios a esa lista. Este artículo explica cómo crear un nuevo módulo que anexará un nuevo país a la lista. Puede revisar el código del módulo de Adobe Commerce Directory existente como referencia. Esto se debe a que el siguiente módulo de ejemplo continúa con el trabajo del módulo Directorio de crear una lista de países y regiones, y reutiliza partes del código de los parches de configuración del módulo Adobe Commerce Directory.

## Documentación recomendada

Debe estar familiarizado con el desarrollo de módulos de Adobe Commerce para crear uno nuevo.

Consulte los siguientes temas en la documentación para desarrolladores antes de intentar crear un módulo nuevo:

* [Guía para desarrolladores de PHP](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/bk-extension-dev-guide.html)
* [Resumen del módulo](https://devdocs.magento.com/guides/v2.4/architecture/archi_perspectives/components/modules/mod_intro.html)
* [Crear un nuevo módulo](https://devdocs.magento.com/videos/fundamentals/create-a-new-module/)
* [Archivos de configuración del módulo](https://devdocs.magento.com/guides/v2.4/config-guide/config/config-files.html)

## Información necesaria

Un nuevo país debe tener un nombre único, ID de país, ISO2 y códigos ISO3 en todo Adobe Commerce.

## Estructura del módulo

En este ejemplo, vamos a crear un nuevo módulo llamado \`ExtraCountries\` con la siguiente estructura de directorio:

(Para obtener más información sobre la estructura del módulo, consulte [Resumen del módulo](https://devdocs.magento.com/guides/v2.4/architecture/archi_perspectives/components/modules/mod_intro.html) en nuestra documentación para desarrolladores).

<pre><ExtraCountries>
 |
 <etc>
 | | | config.xml | di.xml | module.xml |
 <Plugin>
 | | | <Framework>
 | | |   <Locale>
 | | | TranslatedListsPlugin.php |
 <Setup>
 | | | <Patch>
 | | |   <Data>
 | | | AddDataForAbstractCountry.php | composer.json registration.php</pre>

>[!NOTE]
>
>Cada sección del encabezado de este artículo describe los archivos de la sección de estructura del módulo.

## ExtraCountries/etc/config.xml

En este archivo XML se define una nueva configuración de módulo. Las siguientes configuraciones y etiquetas se pueden editar para ajustar la nueva configuración predeterminada del país.

* `allow` - Para añadir el país recién añadido a la lista de &quot;Permitir países&quot; de forma predeterminada, añada el nuevo Código de país al final del `allow` contenido de etiquetas. Los códigos de país están separados por comas. Tenga en cuenta que esta etiqueta sobrescribirá los datos del `Directory` archivo de configuración del módulo *(Directory/etc/config.xml)* `allow` por eso repetimos todos los códigos aquí, además de agregar el nuevo.
* `optional_zip_countries` - Si el código postal del país recién añadido debe ser opcional, añada el código de país al final del contenido de la `optional_zip_countries` etiqueta. Los códigos de país están separados por comas. Tenga en cuenta que esta etiqueta sobrescribirá los datos del `Directory` archivo de configuración del módulo *(Directory/etc/config.xml)* `optional_zip_countries` por eso repetimos todos los códigos aquí, además de agregar el nuevo.
* `eu_countries` - Si el país recién añadido debe formar parte de la lista de países de la Unión Europea de forma predeterminada, añada el código de país al final del contenido de la `eu_countries` etiqueta. Los códigos de país están separados por comas. Tenga en cuenta que esta etiqueta sobrescribirá los datos del `Store` archivo de configuración del módulo *(\_Store/etc/config.xml\_)* `eu_countries` por eso repetimos todos los códigos aquí, además de agregar el nuevo.
* `config.xml` ejemplo de archivo

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <default>
        <general>
            <country>
                <!-- append a new country codes to the end of this list -->
                <allow>AF,AL,DZ,AS,AD,AO,AI,AQ,AG,AR,AM,AW,AU,AT,AX,AZ,BS,BH,BD,BB,BY,BE,BZ,BJ,BM,BL,BT,BO,BQ,BA,BW,BV,BR,IO,VG,BN,BG,BF,BI,KH,CM,CA,CD,CV,KY,CF,TD,CL,CN,CX,CW,CC,CO,KM,CG,CK,CR,HR,CU,CY,CZ,DK,DJ,DM,DO,EC,EG,SV,GQ,ER,EE,ET,FK,FO,FJ,FI,FR,GF,PF,TF,GA,GM,GE,DE,GG,GH,GI,GR,GL,GD,GP,GU,GT,GN,GW,GY,HT,HM,HN,HK,HU,IS,IM,IN,ID,IR,IQ,IE,IL,IT,CI,JE,JM,JP,JO,KZ,KE,KI,KW,KG,LA,LV,LB,LS,LR,LY,LI,LT,LU,ME,MF,MO,MK,MG,MW,MY,MV,ML,MT,MH,MQ,MR,MU,YT,FX,MX,FM,MD,MC,MN,MS,MA,MZ,MM,NA,NR,NP,NL,AN,NC,NZ,NI,NE,NG,NU,NF,KP,MP,NO,OM,PK,PW,PA,PG,PY,PE,PH,PN,PL,PS,PT,PR,QA,RE,RO,RS,RU,RW,SH,KN,LC,PM,VC,WS,SM,ST,SA,SN,SC,SL,SG,SK,SI,SB,SO,ZA,GS,KR,ES,LK,SD,SR,SJ,SZ,SE,CH,SX,SY,TL,TW,TJ,TZ,TH,TG,TK,TO,TT,TN,TR,TM,TC,TV,VI,UG,UA,AE,GB,US,UM,UY,UZ,VU,VA,VE,VN,WF,EH,XK,YE,ZM,ZW,XX</allow>
​
                <!-- if added countries need to belong to the European Union Countries list by default, append their codes to the end of this list -->
                <eu_countries>AT,BE,BG,CY,CZ,DK,EE,FI,FR,DE,GR,HR,HU,IE,IT,LV,LT,LU,MT,NL,PL,PT,RO,SK,SI,ES,SE,GB,XX</eu_countries>
​
                <!-- if added countries are not require zip code, append it's code to the end of this list -->
                <optional_zip_countries>HK,IE,MO,PA,GB,XX</optional_zip_countries>
            </country>
        </general>
    </default>
</config>
```

Para obtener más información sobre los archivos de configuración del módulo, consulte [Guía para desarrolladores de PHP > Definición de archivos de configuración](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/required-configuration-files.html) en nuestra documentación para desarrolladores.

Tenga en cuenta que estos cambios son opcionales y solo afectarán a la pertenencia predeterminada del nuevo país a las listas &quot;Permitir países&quot;, &quot;Código postal es opcional para&quot; y &quot;Países de la Unión Europea&quot;. Si se omite este archivo de la estructura del módulo, se añadirá un nuevo país, pero tendrá que configurarse manualmente en **Administrador** > **Tiendas** > *Configuración* > **Configuración** > **General** > **Opciones de país** página de configuración de.

### ExtraCountries/etc/di.xml

El `di.xml` el archivo configura qué dependencias inserta el administrador de objetos. Consulte <a>Guía para desarrolladores de PHP > The di.xml</a> en nuestra documentación para desarrolladores para obtener más información sobre `di.xml`.

En nuestro ejemplo, debemos registrar un `_TranslatedListsPlugin_` que traducirá los códigos de país recién introducidos a nombres de país completos, si los códigos no están presentes en los datos de localización de la Biblioteca de Zend Locale.

`di.xml` ejemplo

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\Framework\Locale\TranslatedLists">
        <plugin name="Magento_Directory" type="VendorName\ExtraCountries\Plugin\Framework\Locale\TranslatedListsPlugin"/>
    </type>
</config>
```

### ExtraCountries/etc/module.xml

En el archivo de registro del módulo debemos especificar la dependencia para el módulo &quot;Adobe Commerce Directory&quot; asegurándonos de que el módulo &quot;Extra Country&quot; se registre y ejecute después del módulo Directory.

Consulte [Administración de dependencias de módulo](https://devdocs.magento.com/guides/v2.4/architecture/archi_perspectives/components/modules/mod_depend.html#managing-module-dependencies) en nuestra documentación para desarrolladores para obtener más información sobre las dependencias de los módulos.

`module.xml` ejemplo

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
    <module name="VendorName_ExtraCountries" >
        <sequence>
            <module name="Magento_Directory"/>
        </sequence>
    </module>
</config>
```

### ExtraCountries/Plugin/Framework/Locale/TranslatedListsPlugin.php

En el `aroundGetCountryTranslation()` método del complemento debemos traducir un código de país en un nombre de país completo. Este paso es necesario para los países que no tienen un nombre completo asociado con un nuevo código de país en la Biblioteca de configuración regional de Zend.

```php
<?php
namespace VendorName\ExtraCountries\Plugin\Framework\Locale;
​
use Magento\Framework\Locale\ListsInterface;
​
/**
 * Plugin to add full names of added countries that are not included in Zend Locale Data
 */
class TranslatedListsPlugin
{
    /**
     * Get the full name of added countries
     *
     * Since the locale data for the added country may not be present in the Zend Locale Library,
     * we need to provide full country name matching the added code
     *
     * @param ListsInterface $subject
     * @param callable $proceed
     * @param $value
     * @param null $locale
     * @return string
     */
    public function aroundGetCountryTranslation(
        ListsInterface $subject,
        callable $proceed,
        $value,
        $locale = null
    )
    {
        if ($value == 'XX') {
            return 'Abstract Country';
        }
​
        return $proceed($value, $locale);
    }
}
```

### ExtraCountries/Setup/Patch/Data/AddDataForAbstractCountry.php

Este parche de datos se ejecutará durante el proceso de instalación/actualización de Adobe Commerce y añadirá un nuevo registro de país a la base de datos.

Consulte [Desarrollo de parches de datos y esquemas](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/declarative-schema/data-patches.html) en nuestra documentación para desarrolladores para obtener más información sobre los parches de datos.

En el ejemplo siguiente, puede ver que la variable `$data` matriz del método `apply()` contiene los códigos de ID de país, ISO2 e ISO3 para el nuevo país, y estos datos se están insertando en la base de datos.

```php
<?php
namespace Magento\ExtraCountries\Setup\Patch\Data;
​
use Magento\Framework\Setup\ModuleDataSetupInterface;
use Magento\Framework\Setup\Patch\DataPatchInterface;
use Magento\Framework\Setup\Patch\PatchVersionInterface;
​
/**
 * Add Abstract Country data to the country list
 *
 * @package Magento\ExtraCountries\Setup\Patch
 */
class AddDataForAbstractCountry implements DataPatchInterface, PatchVersionInterface
{
    /**
     * @var ModuleDataSetupInterface
     */
    private $moduleDataSetup;
​
    /**
     * @param ModuleDataSetupInterface $moduleDataSetup
     */
    public function __construct(
        ModuleDataSetupInterface $moduleDataSetup
    ) {
        $this->moduleDataSetup = $moduleDataSetup;
    }
​
    /**
     * @inheritdoc
     */
    public function apply()
    {
        /**
         * Fill table directory/country
         */
        $data = [
            ['XX', 'XX', 'XX']
        ];
​
        $columns = ['country_id', 'iso2_code', 'iso3_code'];
        $this->moduleDataSetup->getConnection()->insertArray(
            $this->moduleDataSetup->getTable('directory_country'),
            $columns,
            $data
        );
    }
​
    /**
     * @inheritdoc
     */
    public static function getDependencies()
    {
        return [];
    }
​
    /**
     * @inheritdoc
     */
    public static function getVersion()
    {
        return '0.0.1';
    }
​
    /**
     * @inheritdoc
     */
    public function getAliases()
    {
        return [];
    }
}
```

### ExtraCountries/registration.php

Este es un ejemplo del archivo registration.php. Para obtener más información sobre el registro de módulos, consulte [Guía para desarrolladores de PHP > Registrar su componente](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/component-registration.html) en nuestra documentación para desarrolladores.

```php
<?php
use Magento\Framework\Component\ComponentRegistrar;
​
ComponentRegistrar::register(ComponentRegistrar::MODULE, 'VendorName_ExtraCountries', __DIR__);
```

### ExtraCountries/composer.json

Este es un ejemplo del archivo composer.json.

Para obtener más información sobre composer.json, consulte [Guía para desarrolladores de PHP > El archivo composer.json](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/composer-integration.html) en nuestra documentación para desarrolladores.

```json
{
    "name": "vendor_name/module-extra-countries",
    "description": "A module that adds extra countries to magento directory",
    "type": "magento2-module",
    "license": [
    ],
    "require": {
        "php": "~7.3.0||~7.4.0",
        "lib-libxml": "*",
        "magento/framework": "*",
        "magento/module-directory": "*"
    },
    "autoload": {
        "files": [
            "registration.php"
        ],
        "psr-4": {
            "VendorName\\ExtraCountries\\": ""
        }
    },
    "config": {
        "sort-packages": true
    }
}
```

## Instalación del módulo

Para saber cómo instalar el módulo, consulte [Ubicaciones de módulos](https://devdocs.magento.com/guides/v2.4/architecture/archi_perspectives/components/modules/mod_intro.html#module-locations) en nuestra documentación para desarrolladores.

Una vez que el directorio del módulo se coloque en una ubicación correcta, ejecute `bin/magento setup:upgrade` para aplicar los parches de datos y registrar el complemento de traducción.

Es posible que tenga que limpiar la caché del explorador para que funcionen los nuevos cambios.
