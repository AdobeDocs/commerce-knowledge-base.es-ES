---
source-git-commit: 0cfb7dc0dce68bcb0933a5ae49b0cd5a8b5b5a39
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---
# Guía de validación de metadatos

Para garantizar el formato correcto de los metadatos en los archivos MD, hemos implementado una prueba de validación de metadatos. Este documento proporciona directrices para ayudar a los colaboradores a evitar algunos de los errores de validación de metadatos más comunes.

**Ejemplo de metadatos:**

```markdown
---
title: This is a title
labels: article,labels,tags
---

Article content...
```

## Errores de validación comunes y cómo evitarlos/corregirlos

A continuación se indican algunos de los escenarios más comunes en los que se producen errores de validación de metadatos.

### Dos puntos en los metadatos

Se producirá un error de validación si el título, las etiquetas o ambos tienen dos puntos.

**Ejemplo:**

```markdown
---
title: Patch: Unable to validate VAT number - Adobe Commerce on cloud infrastructure
labels: patch: 2041.1,article,labels,tags
---
```

Para evitar este error, ajuste el título o las etiquetas (o ambos si tienen dos puntos) en **comillas simples**.

**Ejemplo:**

```markdown
---
title: 'Patch: Unable to validate VAT number - Adobe Commerce on cloud infrastructure'
labels: 'patch: 2041.1,article,labels,tags'
---
```

### Dos puntos y comillas simples o apóstrofo en los metadatos

La solución anterior no funcionará si el título o las etiquetas contienen dos puntos, comillas simples o apóstrofos.

**Ejemplo:**

```markdown
---
title: Patch: Can't validate 'VAT' number - Adobe Commerce on cloud infrastructure
labels: patch: 2041.1,'article',labels,tags
---
```

Este error se corrige ajustando el título o las etiquetas (o ambos) en **comillas dobles**.

**Ejemplo:**

```markdown
---
title: "Patch: Can't validate 'VAT' number - Adobe Commerce on cloud infrastructure"
labels: "patch: 2041.1,'article',labels,tags"
---
```

### Dos puntos, comillas dobles y comillas simples o apóstrofo en los metadatos

**Ejemplo:**

```markdown
---
title: Patch: Can't validate 'VAT' number - Adobe "Commerce" on cloud infrastructure
labels: patch: 2041.1,'article',"labels",can't,tags
---
```

Cuando esto sucede, ajuste el título o las etiquetas (o ambos) en **comillas dobles** y use un **barra invertida** para omitir todas las comillas dobles del título y las etiquetas.

**Ejemplo:**

```markdown
---
title: "Patch: Can't validate 'VAT' number - Adobe \"Commerce\" on cloud infrastructure"
labels: "patch: 2041.1,'article',\"labels\",can't,tags"
---
```

### Faltan campos en los metadatos

Se producirá un error de validación si falta el campo Título o el campo Etiquetas en los metadatos.

**Ejemplo:**

```markdown
---
title: This is a title
---
```

O

```markdown
---
labels: article,labels,tags
---
```

Para evitar este error, incluya ambos campos en los metadatos.

El campo de etiquetas se puede dejar vacío y no producirá un error, pero el campo de título debe rellenarse.

**Ejemplo:**

```markdown
---
title: Unlike labels the title field must be filled
labels:
---
```
