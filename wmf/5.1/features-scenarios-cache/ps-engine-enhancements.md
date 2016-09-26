---
title: Mejoras en el motor de PowerShell
author: jasonsh
translationtype: Human Translation
ms.sourcegitcommit: 47c963343c541d0f2ace194f365de5fcd809ccc5
ms.openlocfilehash: 1b35a25312b44d14ec8771be9e17aaa43e270b61

---

# Mejoras en el motor de PowerShell #

Se han implementado las siguientes mejoras al motor central de PowerShell para PowerShell 5.1:


## Rendimiento ##

El rendimiento ha mejorado en algunas áreas importantes:

1. Inicio
2. La canalización en cmdlets como ForEach-Object y Where-Object es aproximadamente un 50 % más rápido 

Algunas mejoras de ejemplo (los resultados pueden variar en función del hardware): 

| Escenario | Tiempo de 5.0 (ms) | Tiempo de 5.1 (ms) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| Primera ejecución de PowerShell: `powershell -command "Unknown-Command"` | 30000 | 13000 |
| Caché de análisis de comandos integrada: `powershell -command "Unknown-Command"` | 7000 | 520 |
| <code>1..1000000 &#124; % { }</code> | 1400 | 750 |
  
Un cambio relacionado con el inicio puede afectar a algunos escenarios no compatibles. PowerShell ya no lee los archivos `$pshome\*.ps1xml`: estos archivos se han convertido en C# para evitar la sobrecarga de archivos y de la CPU que supone procesar los archivos XML. Los archivos aún existen para proporcionar compatibilidad con V2 en paralelo, por lo que si se cambia el contenido de los archivos, esto no tendrá ningún efecto en V5, solo en V2. Tenga en cuenta que el cambio del contenido de estos archivos nunca ha sido un escenario compatible.

Otro cambio visible es la forma en que PowerShell almacena en caché tanto comandos exportados como otra información de los módulos instalados en un sistema. Antes, la memoria caché se almacenaba en el directorio `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`. En WMF 5.1, la memoria caché es un único archivo `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Para más información, consulte [analysis_cache.md]().

A partir de la versión 5.1, PowerShell está disponible en diferentes ediciones que denotan distintos conjuntos de características y compatibilidad con varias plataformas.



## Correcciones de errores ##

Se han corregido los siguientes errores importantes:

### La detección automática de módulos usa plenamente `$env:PSModulePath` ###

La detección automática de módulos (carga de módulos automáticamente sin un cmdlet Import-Module explícito al llamar a un comando) se introdujo en WMF 3. Cuando se introdujo, PowerShell comprobaba los comandos en `$PSHome\Modules` antes de usar `$env:PSModulePath`.

WMF 5.1 cambia este comportamiento para usar `$env:PSModulePath` completamente. Esto permite que un módulo creado por el usuario que define los comandos que proporciona PowerShell (por ejemplo, `Get-ChildItem`) se cargue automáticamente y reemplace correctamente el comando integrado.

### El redireccionamiento de archivos deja de integrar como parte del código `-Encoding Unicode` ###

En todas las versiones anteriores de PowerShell, era imposible controlar la codificación de archivos usada por el operador de redireccionamiento de archivos (p. ej., `Get-ChildItem > out.txt` porque PowerShell agregó `-Encoding Unicode`).

A partir de WMF 5.1, se puede cambiar la codificación de archivos del redireccionamiento mediante el establecimiento de `$PSDefaultParameterValues`, p. ej.

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### Se ha corregido una regresión en el acceso de los miembros de `System.Reflection.TypeInfo` ###

Una regresión introducida en WMF 5 interrumpía el acceso de los miembros de `System.Reflection.RuntimeType`, por ejemplo, `[int].ImplementedInterfaces`.
Este error se ha corregido en WMF 5.1.


### Se han corregido algunos problemas con objetos COM ###

WMF 5 introdujo un nuevo enlazador COM para invocar métodos en objetos COM y acceder a propiedades de objetos COM.
Este nuevo enlazador ha mejorado considerablemente el rendimiento, pero también ha presentado algunos errores que se han corregido en WMF 5.1.

#### Las conversiones de argumentos no siempre se realizaban correctamente ####

En el ejemplo siguiente:

```
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

El método SendKeys espera una cadena, pero PowerShell no ha convertido el carácter en una cadena, lo que aplaza la conversión a IDispatch:: Invoke, que usa VariantChangeType para realizar la conversión, lo que en este ejemplo provocó el envío de las claves '1', '7' y '3', en lugar de la clave Volume.Mute, que era la que se esperaba.

#### Los objetos COM enumerables no siempre se controlan correctamente ####

PowerShell normalmente enumera la mayoría de los objetos enumerables, pero una regresión introducida en WMF 5 impidió la enumeración de objetos COM que implementan IEnumerable.  Por ejemplo:

```
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

En el ejemplo anterior, WMF 5 escribió incorrectamente Scripting.Dictionary en la canalización, en lugar de enumerar los pares clave/valor.


### `[ordered]` no se permitía en las clases ###

WMF5 introdujo clases con una validación de los literales de tipo que se usan en las clases.  `[ordered]` parece un literal de tipo, pero no es un verdadero tipo .NET.  WMF5 informaba incorrectamente de un error en `[ordered]` dentro de una clase:

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### Los temas de ayuda con varias versiones no funcionan ###

Antes de WMF 5.1, si había varias versiones de un módulo instaladas y todas compartían un tema de ayuda, por ejemplo, about_PSReadline, `help about_PSReadline` devolvía varios temas sin ninguna forma obvia de ver la ayuda real.

WMF 5.1 corrige este problema, para lo que devuelve la ayuda de la versión más reciente del tema.

Get-Help no proporciona una manera de especificar de qué versión desea obtener ayuda, por lo que la solución alternativa es navegar hasta el directorio de módulos y ver la ayuda directamente con una herramienta como su editor favorito. 



<!--HONumber=Sep16_HO3-->


