# <a name="style-guide-for-powershell-docs"></a>Guía de estilo para PowerShell-Docs


## <a name="titlesheadings"></a>Títulos y encabezados

* Los títulos y encabezados (todo antecedido por \#) deben ir seguidos de una línea nueva
* Solo se debe poner en mayúsculas la primera letra de un título y de todos los nombres propios de ese título
* Solo 1 H1 por documento
* Al editar el contenido de referencia, platyPS recomienda H2 y no se deben agregar o quitar, ya que provocaría una interrupción de la compilación
* Use solo \# encabezados de estilo (en lugar de = o encabezados de estilo \-)

### <a name="correct"></a>Correcto

```
# Header 1

## Header 2

### Header 3

```

### <a name="incorrect"></a>Incorrecto

```
Header 1
========

Header 2
--------

### Header 3
```

## <a name="syntax"></a>Sintaxis

* Cuando hablamos de un cmdlet en el párrafo, utilice \` para resaltar los nombres de cmdlet
  * Al escribir un artículo (en lugar de contenido de referencia), la primera instancia de un nombre de cmdlet debe ser un vínculo a la documentación de dicho cmdlet
* Todos los bloques de sintaxis de PowerShell deben usar &#96;&#96;&#96;powershell
* No inicie comandos de PowerShell con "C:\ PS>"
* La salida emitida por comandos de PowerShell debe incluir comentarios para evitar que reciba el resaltado de sintaxis
* Los nombres de propiedad y de parámetro deben estar en **negrita**


## <a name="lists"></a>Listas

* No terminar elementos de lista con un punto (a menos que contengan varias oraciones)
* Si la lista contiene varias oraciones, considere la posibilidad de usar un encabezado 3/4/5 (según corresponda) debajo de la idea principal

## <a name="links"></a>Vínculos

* Los vínculos siempre se marcan mediante la sintaxis MarkDown `[friendlyname](url)`
* Los vínculos deben tener un nombre descriptivo cuando sea posible, muy probablemente el título de la página vinculada
  * **Excepción**: vínculos hacia los sitios que no son de Microsoft solo deben tener una dirección URL
* Todos los elementos de la sección "vínculos relacionados" que se encuentra en la parte inferior deben ser hipervínculos. 

## <a name="line-breaks"></a>Saltos de línea

* Debe incluir saltos de línea semánticos
* Debe limitar las líneas a 100 caracteres (elemento abierto: herramientas para ayudarnos a validar esto)
* PUEDE quitar saltos de línea adicionales de PS4 +, NO ps3 (necesita validarse)
