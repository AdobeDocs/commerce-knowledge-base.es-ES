---
source-git-commit: c587986edc925c49bf95ab935888b59f265371af
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---
# Guía de formato KB

## Autor en Markdown

Por lo general, utilizamos la [Guía de estilo de sintaxis de Adobe Experience League Markdown](https://experienceleague.adobe.com/docs/authoring-guide-exl/using/markdown/syntax-style-guide.html?lang=es), pero existen algunas diferencias y excepciones. Además, en determinados casos se requieren determinadas etiquetas de HTML.

Los siguientes son ejemplos del formato Markdown que se utiliza más comúnmente en nuestro repositorio.

## Formato básico

Para aplicar negrita al texto, escríbalo entre dos asteriscos:

`This will be **bold** text`

Para aplicar cursiva al texto, utilice un solo asterisco:

`This text will be *italics*`

Para aplicar formato subrayado al texto, use la etiqueta `<ins>`:

`<ins>This text will be underlined</ins>`

Para agregar un salto de línea, use la etiqueta de HTML `<br>`.


## Encabezados

Utilice el siguiente formato para encabezados de H2 a H5. H1 nunca se utiliza, ya que el título del artículo se considera H1.

`## Header 2 `

`### Header 3 `

`#### Header 4`

`##### Header 5`

## Bloques y elementos en línea de código

Utilice una sola comilla invertida para adjuntar el elemento de código que desee resaltar:

Es \`inline code\` dentro de un párrafo de texto.

### Bloques de código

Para insertar un bloque de código, encierre el bloque de código entre comillas triples y especifique el idioma después de abrir estas:

\`\`\` sql

SELECCIONAR TABLE_NAME COMO `Table`,
ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM: information_schema.TABLES
WHERE TABLE_SCHEMA = &quot;%project_id%&quot;
ORDENAR POR (DATA_LENGTH + INDEX_LENGTH) DESC;

\`\`\`

Esto se representará como:

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "%project_id%"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

Según nuestras reglas de vinculación, siempre debe especificar un idioma para el bloque de código.

Para ver la lista de idiomas admitidos, consulte https://github.com/github/linguist/blob/master/lib/linguist/languages.yml.

Si el resaltado no funciona para un determinado idioma en Markdown (es decir, el idioma no es compatible), para que al menos esté resaltado cuando se publique en https://support.magento.com/hc/en-us/, utilice el siguiente HTML:

```html
<pre><code class="language-%language-code%"
your code here
</pre></code>
```

Donde ``%language-code%`` son los códigos definidos por [idiomas compatibles con Prisma.js](https://prismjs.com/#supported-languages).

## Listas

Separe siempre las listas del resto del contenido con líneas en blanco. Las listas deben ir precedidas y seguidas de una línea en blanco.

Utilice el siguiente formato para las listas ordenadas:

```markdown
1. First numbered list item.
1. Second numbered list item.
...
1. Last numbered list item.
```

Para crear una lista con viñetas sin ordenar, empiece una línea con *, + o -. Pero seleccione un método y utilícelo de forma coherente en todo el artículo.

Ejemplo:

```markdown
* Unordered list item.
* Unordered list item.
---
* Last unordered list item.
```

Para añadir contenido entre los elementos de la lista, añada 4 espacios al principio de la línea:

```markdown
* List item.
* List item.
    Here's some content between list items.
* Here we continue the list
```

También puede incrustar listas de esta manera.

## Vínculos

Los vínculos externos son directos:

```markdown
[Adobe](https://www.adobe.com)
```

### Vínculos a archivos adjuntos

Cualquier tipo de archivo adjunto debe tener los formatos .png, .jpg y .jpeg. Por motivos de seguridad, solo aceptamos archivos adjuntos que estén en uno de los tres formatos.

Para insertar una imagen, coloque la imagen en la subcarpeta *assets* en la misma carpeta de sección que el artículo y utilice la siguiente sintaxis para insertar la imagen en el artículo:

```markdown
![alt text](assets/image.png)
```

Si desea personalizar el tamaño de la imagen, deberá hacerlo con la siguiente etiqueta de HTML:

```html
<img src = "assets/image.png" alt = "your alt text" width="custom width, ex: 250px">
```

```markdown
[asset_title](assets/%file_name%).
```

### Vínculos a secciones específicas del artículo

Si necesita hacer referencia a una sección dentro del artículo, no necesita crear un anclaje independiente. Se generan automáticamente al publicar todos los encabezados H2-H6. Los anclajes se generan a partir del encabezado haciendo que todas las palabras estén en minúsculas y usando &quot;-&quot; para separar las palabras.

Ejemplo:

```markdown
## This is header
```

Este es un vínculo a este encabezado:

```markdown
[this is link to the anchor in the same article](#this-is-header)
```

Si necesita hacer referencia a un elemento que no sea un encabezado, use el HTML para definir el elemento que desea agregar y use [id atributo](https://www.w3schools.com/html/html_id.asp). A continuación, puede utilizar Markdown o HTML para hacer referencia a este ID.

### Vínculos relativos y vínculos a otros artículos

No utilice vínculos relativos para hacer referencia a los artículos de nuestra base de conocimiento de soporte. Esos vínculos no funcionarán cuando tu artículo se publique en el [Centro de ayuda de Adobe Commerce](https://support.magento.com/hc/en-us).
Use hipervínculos completos del [Centro de ayuda de Adobe Commerce](https://support.magento.com/hc/en-us).


## Tablas

Usar formato de HTML [para tablas](https://www.w3schools.com/html/html_tables.asp).


## Advertencias y bloques de información

Bloque de notas de éxito:

```
>![success]
>
>This is a success note
```

Bloque de advertencia:

```
>![warning]
>
>This is a warning
```

Bloque de notas informativas:

```
>![info]
>
>This is a block with additional info
```
