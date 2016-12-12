# <a name="contributing-to-powershell-documentation"></a>Contribuir a la documentación de PowerShell

Gracias por su interés en la documentación de PowerShell. Consulte el contenido que aparece a continuación para obtener información sobre cómo contribuir a la documentación técnica.

>Para obtener información general acerca de cómo empezar a usar Git y GitHub, consulte [Ayuda de GitHub](https://help.github.com/). 

## <a name="sign-a-cla"></a>Firmar un CLC

Antes de contribuir a cualquiera de los repositorios de PowerShell, deberá [firmar un contrato de licencia de contribución (CLC) de Microsoft](https://cla.microsoft.com/). Si ya ha contribuido a los repositorios de PowerShell en el pasado, ¡enhorabuena! Ya ha completado este paso.

## <a name="providing-feedback-on-powershell-documentation"></a>Proporcionar comentarios sobre la documentación de PowerShell

Puede señalar errores, sugerir cambios o solicitar nuevos temas [creando un problema](https://help.github.com/articles/creating-an-issue/) en la [página de problemas del repositorio PowerShell-Docs](https://github.com/PowerShell/PowerShell-Docs/issues).

Los miembros del equipo de documentación de PowerShell revisan los problemas con regularidad y los clasifican, asignan y abordan consecuentemente.

## <a name="writing-powershell-documentation"></a>Escribir documentación de PowerShell

Una de las formas más sencillas de contribuir a PowerShell es ayudando a escribir y editar la documentación. Toda la documentación que alojada en GitHub está escrita con [GitHub Flavored Markdown](https://help.github.com/articles/github-flavored-markdown/).

## <a name="making-minor-edits-to-existing-topics"></a>Realizar cambios menores en temas existentes

Para [modificar un archivo existente](https://help.github.com/articles/editing-files-in-another-user-s-repository/), simplemente vaya hasta él y haga clic en el botón Editar. GitHub crea automáticamente su propia bifurcación del repositorio, donde puede realizar los cambios. Una vez que haya terminado, guarde los cambios y envíe una [solicitud de incorporación de cambios](https://help.github.com/articles/creating-a-pull-request/) a la rama *staging* del repositorio [PowerShell-Docs](https://github.com/PowerShell/PowerShell-Docs). Una vez creada su solicitud de incorporación de cambios, un miembro del equipo de documentación de PowerShell revisará sus cambios antes de incorporarlos a la rama *staging*.

## <a name="making-major-edits-to-existing-topics"></a>Realizar cambios importantes en temas existentes

Si va a realizar cambios importantes en un artículo existente, agregar o cambiar imágenes, o contribuir a un artículo nuevo, debe crear manualmente la bifurcación de GitHub y, a continuación, clonar la bifurcación en el equipo local. Una bifurcación es una réplica del repositorio principal basada en GitHub y asociada a su cuenta de GitHub que le proporciona una copia de trabajo que puede usar de forma aislada. Va a crear solicitudes de extracción desde la bifurcación. De forma similar, un clon es una réplica del repositorio basada en local que, en este caso, será un clon de la bifurcación. El clon le permite trabajar en repositorios de Git sin conexión y con herramientas y software nativos más potentes.

Este es el flujo de trabajo para realizar cambios importantes en documentación existente:

1. [Cree una bifurcación](https://help.github.com/articles/fork-a-repo/) del repositorio [PowerShell-Docs](https://github.com/PowerShell/PowerShell-Docs).
2. [Cree un clon de la bifurcación](https://help.github.com/articles/cloning-a-repository/) en el equipo local.
3. Cree una nueva rama local en el repositorio clonado.
4. Realice los cambios en el archivo o los archivos que quiera actualizar con un editor Markdown. 
   Consulte el listado de los editores Markdown más utilizados que aparece más abajo.
5. [Incorpore los cambios de la rama local](https://help.github.com/articles/pushing-to-a-remote/) en la bifurcación.
6. [Cree una solicitud de incorporación de cambios](https://help.github.com/articles/creating-a-pull-request/) a la rama *staging* del repositorio de [PowerShell-Docs](https://github.com/PowerShell/PowerShell-Docs).

## <a name="creating-new-topics"></a>Crear temas nuevos

Si desea contribuir nueva documentación, busque primero [problemas con la etiqueta "in progress"](https://github.com/PowerShell/PowerShell-Docs/labels/in%20progress) para evitar la duplicación de esfuerzos.
Si nadie está trabajando en lo que ha planeado:

* Abra un nuevo problema y etiquételo como "in progress" (si es miembro de la organización de PowerShell) o agregue "in progress" como comentario para comunicar a los demás en qué está trabajando
* Siga el mismo flujo de trabajo descrito más arriba para realizar cambios importantes a temas existentes.
* Edite el tema `TOC.md` (ubicado en la carpeta de nivel superior para cada conjunto de documentación) para agregar los nuevos temas a la tabla de contenido. 
  Determine dónde debe ubicarse el nuevo tema en la tabla de contenido y agregue un encabezado del nivel adecuado junto con un vínculo a al tema (`[My topic title](relative path to my topic)`).

## <a name="markdown-editors"></a>Editores Markdown

Estos son algunos editores Markdown que puede probar:

* [Visual Studio Code](https://code.visualstudio.com)
* [Markdown Pad](http://markdownpad.com/)
* [Atom](https://atom.io/)
* [Sublime Text](http://www.sublimetext.com/)


## <a name="github-flavored-markdown-gfm"></a>GitHub Flavored Markdown (GFM)

Todos los artículos de este repositorio, utilizan [GitHub Flavored Markdown (GFM)](https://help.github.com/articles/github-flavored-markdown/).

Estos son algunos elementos básicos de la sintaxis de GMF:

* **Saltos de línea vs. párrafos:** en Markdown no hay `<br />` HTML o elemento `<p />`. En su lugar, los nuevos párrafos se designan con una línea vacía entre dos bloques de texto.

> **Nota**: Agregue una nueva línea única después de cada oración para simplificar la salida de la línea de comandos de diferencias e historial.
Actualmente, esto no está adoptado en todo PowerShell-Docs, pero trabajaremos para que lo esté con el tiempo. No dude en ayudarnos. 

* **Cursiva:** el elemento HTML `<em>some text</em>` se escribe como `*some text*`
* **Negrita:** el elemento HTML `<strong>some text</strong>` se escribe como `**some text**`
* **Títulos:** los títulos en HTML se designan utilizando caracteres `#` al principio de la línea. 
  El número de caracteres `#` corresponde al nivel jerárquico de los títulos (por ejemplo, `#` = `<h1>` y `###` = ```<h3>```).
* **Listas numeradas:** para hacer una lista numerada (ordenada), empiece la línea con `1. `.  
  Si quiere incluir varios elementos dentro de un elemento de lista único, formatee la lista tal como se indica a continuación:
```        
1.  For the first element (like this one), insert a tab stop after the 1. 

    To include a second element (like this one), insert a line break after the first and align indentations.
```
para obtener esta salida:

1.  Para el primer elemento (como esta), inserte un punto de tabulación después del 1. 

    Para incluir un segundo elemento (como este), insertar un salto de línea después de la primera y alinee las sangrías.

* **Listas con viñetas:** las listas con viñetas (desordenadas) son casi idénticas a las listas ordenadas, excepto que el `1. ` se reemplaza por `* `, `- `, o `+ `. Las listas de varios elementos funcional igual que las listas ordenadas.
* **Vínculos:** la sintaxis de un hipervínculo es `[visible link text](link URL)`.
* **Vínculo a otro tema dentro del mismo docset:** un docset es una carpeta de nivel superior dentro de este repositorio (por ejemplo, "dsc", "scripting").
    La sintaxis de un hipervínculo a un tema dentro del mismo docset es `[topic title](relative path to topic)`. 
    Para obtener más información, consulte [Vínculos relativos en los archivos LÉAME](https://help.github.com/articles/relative-links-in-readmes/). 
    Para vincular a un tema que se encuentra en una carpeta de nivel superior distinta, utilice la dirección URL de la página publicada, tal como se describe más arriba.
