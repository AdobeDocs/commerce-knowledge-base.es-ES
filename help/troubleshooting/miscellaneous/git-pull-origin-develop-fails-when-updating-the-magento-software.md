---
title: el desarrollo de git pull origin falla al actualizar el software de Adobe Commerce
description: Este artículo proporciona una corrección para los casos en los que no se puede actualizar el software de Adobe Commerce al ejecutar "git pull origin development".
exl-id: b133253e-c160-4f15-a9b0-8591e93a1e9b
feature: Upgrade
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# el desarrollo de git pull origin falla al actualizar el software de Adobe Commerce

Este artículo proporciona una corrección para los casos en los que no se puede actualizar el software de Adobe Commerce al ejecutar `git pull origin develop`.

## Detalles

Uno de los pasos para actualizar el software de Adobe Commerce es actualizar el repositorio local ejecutando:

```bash
$ git pull origin develop
```

Se puede mostrar el siguiente error:

```terminal
error: Your local changes to the following files would be overwritten by merge:
<list of files>
```

Para saber qué archivos están sujetos a sobrescritura, lea el mensaje o escriba:

```bash
git status
```

En la siguiente sección se analizan las soluciones sugeridas.

### Soluciones sugeridas

La solución depende de si ha modificado o no intencionadamente los archivos en el sistema de archivos de Adobe Commerce. Consulte una de las siguientes secciones para obtener más información.

#### Ha modificado archivos intencionadamente

Resuelva manualmente los conflictos de la forma habitual. Si no está seguro de qué hacer, consulte la [ayuda de GitHub](https://help.github.com/).

#### No ha modificado ningún archivo de forma intencionada

Pruebe cualquiera de las siguientes opciones:

* Si está seguro de que no ha modificado ningún archivo y no le importa quitar o sobrescribir los cambios en el sistema de archivos de Adobe Commerce, escriba:

  </p>
    <pre><code class="language-bash">$ git reset --hard HEAD && git pull origin develop</code></pre>

  Después, continúe donde lo dejó con la actualización de Adobe Commerce.

* Es posible que una configuración de GitHub pueda evitar estos errores en el futuro. De forma predeterminada, GitHub almacena contenido mediante los caracteres finales de línea predeterminados del sistema operativo. Si utiliza Linux, pero otro colaborador ha confirmado un cambio con Windows, GitHub convierte los finales de línea de Windows a Linux cuando clona o extrae. Esto da la apariencia de un cambio en los archivos cuando, de hecho, no se realizó ningún cambio.

  Para configurar GitHub para que ignore los extremos de línea, introduzca el siguiente comando en su cliente Git:

  </p>
    <pre><code class="language-bash">$ git config --system core.autocrlf false</code></pre>

  Si utiliza Windows, escriba:

  </p>
    <pre><code class="language-bash">$ git config --system core.eol LF</code></pre>

  >[!NOTE]
  >
  >El Adobe no recomienda ni respalda ninguna configuración de GitHub en particular. Los anteriores son solo sugerencias. Para obtener más información, consulte la [ayuda de GitHub](https://help.github.com/).

  Continúe donde lo dejó con la actualización de Adobe Commerce.
