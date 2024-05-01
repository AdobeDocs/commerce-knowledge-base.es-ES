---
source-git-commit: c992521cae8c847adc0cc23d2323300e0ba69cdc
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---
# Guía de estilo KB de soporte

Siga estas recomendaciones de estilo y formato al contribuir al Centro de ayuda de Adobe Commerce.

## Títulos

* Los títulos aparecen en mayúsculas como en una oración.
* Plural para títulos; singular para encabezados de procedimiento. Ejemplo: Título - Escritura de libros. Encabezado - Escribe un libro.
* Utilice títulos cortos, con palabras importantes al principio. Por razones de SEO, es muy recomendable que los títulos no tengan más de 70 caracteres (hay una excepción cuando una reducción del título impide que se comunique el verdadero significado). 

## Encabezados

* El encabezado de nivel superior es H2. (H1 es el título de artículo predeterminado, aunque el título no tenga un formato visible con H1).
* Utilice verbos infinitos para los encabezados de tarea. Por ejemplo, &quot;Cómo identificar eventos de alto tráfico&quot;.
* Utilice el formato singular para encabezados de tarea. Por ejemplo, &quot;Estructura del módulo&quot;.
* Evite encabezados dobles (debe haber al menos una frase entre los encabezados).
* Mayúsculas como en una oración para todos los encabezados.
* Los títulos de las tareas son obligatorios (&quot;Crear x&quot;, no &quot;Crear x&quot; o &quot;Crear x&quot;).

## Listas

* Pasos de una tarea: máximo 9

* Las listas con viñetas facilitan el análisis.

   * Utilice listas con viñetas para métodos, enfoques, opciones y pasos de tareas no consecutivos.
   * Utilice viñetas cortas para escribir texto, preferiblemente no más de dos frases.
   * Reduzca al máximo el número de viñetas; lo ideal es disponer de siete o menos.
   * Evite colocar una sugerencia o nota entre elementos con viñetas.
   * Utilice una estructura gramatical paralela en las listas, pero rompa esta regla si resulta en un exceso de lenguaje verbal o sobre pilotes.
   * Ponga en mayúscula la primera palabra de cada elemento en una lista con viñetas, incluso si es un fragmento.

* Haga que las listas sean paralelas. Por ejemplo, cada elemento debe ser un sustantivo o una frase que comience con un verbo.

## Notas y sugerencias

Guarde las notas y sugerencias en un solo párrafo. La necesidad de más de un párrafo indica la necesidad de reestructurar el contenido e incluirlo en el cuerpo del artículo.

## Capitalización

Cuando haya dudas, no use mayúsculas. En los encabezados, utilice mayúsculas como en una oración. Ponga en mayúsculas los sustantivos propios y la primera palabra después de dos puntos.

## Elementos de IU

* Todo lo que hace clic el usuario coloca en **negrita**. Por ejemplo, &quot;Haga clic en **Continuar**.&quot; Los valores de opción y los mensajes de error tienen el formato _cursiva_.
* Siempre que sea posible, evite mencionar el tipo de elemento de la interfaz de usuario en las instrucciones. (Haga clic en **Siguiente**. frente a Haga clic en **Siguiente** botón.)
* Utilice &quot;Choose&quot; y &quot;>&quot; en las secuencias de comandos. (Seleccionar **Editar** > **Preferencias**. frente a Haga clic en Editar | Preferencias.)
* Preposición: &quot;en&quot; para el cuadro de diálogo, la ventana, son un, panel, vista, asistente, lista, carpeta, nodo.
* Preposición: &quot;activado&quot; para pantalla, página, barra de herramientas, barra de menús, pestaña, panel, cinta de opciones.
* Preposición: clic (clic) **Siguiente** frente a hacer clic en **Siguiente**).

## Nombres de archivo

Los nombres de archivo y las carpetas tienen formato de código. Ejemplo: El `/var/log` el directorio del sistema contiene registros para todos los entornos.


## Números

Sobre todo, las reglas de consistencia al aproximarse a los números escritos frente a los números.

Escriba un número, como &quot;cinco&quot; o &quot;nueve&quot; cuando el número sea menor que 10 (números del uno al nueve).

Escriba un número como un número, como &quot;42&quot; u &quot;11&quot;, cuando:

* El número es mayor que 9 (números diez y superiores).
* Está especificando el número:
   * Dentro de una línea de código o fragmento de código.
   * Dentro de una ruta de archivo o nombre de directorio.
   * Al comunicar un intervalo, como &quot;entre 5 y 25&quot; o &quot;revise los números del 8 al 21&quot;.
   * Los números han sido medidos o calculados como &quot;62 picas&quot; o &quot;830 MHz&quot;.

Utilice una mezcla de números y números al anotar una cantidad de cosas numeradas, como &quot;una colección de quince ejecuciones de 1000 ensayos&quot;.

Escriba ambos números en palabras o ambos en números, si tiene dos números en una oración, uno bajo 10 (como 4) y uno sobre 10 (como 14). Por ejemplo, aquí se usan números: &quot;14 minutos por cada 4 litros de líquido&quot;.


## Casos particulares de redacción

<table class="relative-table" style="width: 100.0%;"><colgroup><col style="width: 12.003596%;"> <col style="width: 16.444849%;"> <col style="width: 71.55351%;"></colgroup>

<tbody>

<tr>

<th>Incorrecto</th>

<th>Correcto</th>

<th> Razonar
</th>

</tr>

<tr>

<td>Inicie sesión en la página de cuenta de Magento.com. </td>

<td>Inicie sesión en su cuenta de Adobe Commerce</td>

<td colspan="1">
</td>

</tr>

<tr>

<td>Extensiones de terceros (módulos)</td>

<td>extensiones de terceros (módulos)</td>

<td colspan="1">
</td>

</tr>

<tr>

<td>Fragmentos de código SQL</td>

<td>Las sentencias están en mayúsculas (SELECT frente a select)</td>

<td colspan="1">Mejor legibilidad</td>

</tr>

<tr>

<td colspan="1">

Referencias a otros recursos.

Ejemplo: consulte xyz en la documentación para desarrolladores


</td>

<td colspan="1">Consulte xyz en nuestra documentación para desarrolladores</td>

<td colspan="1">

Requisito de accesibilidad: todos los vínculos describen el destino del vínculo.


</td>

</tr>

<tr>

<td colspan="1">

Adobe Commerce v2.4.0

Adobe Commerce 2.4.0

Adobe Commerce versión 2.4.0

</td>

<td colspan="1">Adobe Commerce 2.4.0 (sin versión o versión)</td>

<td colspan="1"></td>

</tr>

<tr>

<td colspan="1">

2.4.x

2.4.X

</td>

<td colspan="1">

2.4.0

2.4.x

</td>

<td colspan="1">

No hay razón para mayúsculas.

</td>

</tr>

<tr>

<td colspan="1">

Mensaje de error: _&quot;Se ha producido un error.&quot;_

Mensaje de error: __Se ha producido un error.__

</td>

<td colspan="1"> Mensaje de error:  <i>Se ha producido un error.</i> </td>

<td colspan="1">
</td>

</tr>

</tbody>

</table>

## Accesibilidad

* Todos los elementos gráficos o no textuales tienen equivalentes textuales o texto alternativo. Ejemplo: ![example_image](/url "alt_text_for_this_image").

* Todos los vínculos describen el destino del vínculo. Ejemplo [vincular](/uri "destination_of_the_link").


<!--
## Accessible tables

Use tables for information that is best presented along two axes (rows and columns). Do not use tables when a list or definition list serves the purpose. If using tables, follow these recommendations:

*   Headers for rows and columns; row headers easier for screen readers.

*   Simple linear construction.

*   Content within cells consistently structured.  -->


## Lenguaje abusivo

* Evite el lenguaje abusivo. 
* Evite el lenguaje racista o &quot;podría sentirse como racista&quot;.
* Evite el lenguaje con fuertes connotaciones negativas o fuertes colores emocionales, como &quot;matar&quot;, &quot;terminar&quot;.


## Vínculos 

La mayoría de los vínculos aparecen en listas de vínculos dentro del artículo. Evite los vínculos en línea innecesarios.

Una práctica recomendada es aislar los vínculos en línea en una lista de vínculos con un título configurable.

Al final de un artículo aparece únicamente una lista de vínculos especializados, denominada lista de vea-también.    Utilice las listas de vínculos de forma estratégica, solo es necesario. Como regla general, no más de seis vínculos en una lista de vínculos.

### Vínculos a sitios web externos

Utilice direcciones URL normales en lugar de goURL para vincular páginas de fuera de  [Adobe.com](http://Adobe.com).


## Comas

En general, siga las recomendaciones del Manual de estilo de Chicago para la puntuación de estilo abierto, puntuando solo cuando sea necesario para evitar malinterpretaciones. Por ejemplo, puede omitir la coma antes de una conjunción en una oración compuesta si hay poco o ningún riesgo de malinterpretar. Utilice la coma donde sea necesario para una aclaración.

* Utilice siempre la coma de serie (una coma que preceda a _y_ o _o_ en una lista de tres o más elementos): x, y y z

* Coloque una coma antes de una conjunción que introduzca una cláusula independiente: &quot;Especifique una ubicación y escriba un nombre para la lista de archivos&quot;.

* No separe las diferencias de plataforma con una coma: &quot;... Ctrl (Windows) o Comando (Mac OS)&quot;

* Utilice siempre una coma después de una frase introductoria o cláusula: &quot;En Photoshop, importe el archivo Illustrator&quot;.

## Versiones

* Utilizamos &quot;versión&quot; para todas las versiones (principal/menor/parche). Por ejemplo, &quot;Versiones compatibles: Adobe Commerce 2.3.x&quot;

* Utilizamos la minúscula &quot;x&quot; al escribir sobre todas las versiones de parches dentro de una versión menor y todas las secundarias con una versión principal. Por ejemplo, Adobe Commerce 2.x.x.

## Marca

* El Magento Commerce ahora es Adobe Commerce. Consulte la [Cambiar marca de términos](https://github.com/magento/knowledge-base/wiki) wiki para obtener más información sobre cómo utilizar un idioma de promoción de la marca actualizado.
