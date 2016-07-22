---
title: "Corrección de errores de WMF 5.1 (versión preliminar)"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 90d57af0c8b90e709769525455ae39557b9c7176

---

# Corrección de errores de WMF 5.1 (versión preliminar)#

## Correcciones de errores ##

Se han corregido los siguientes errores importantes en WMF 5.1:

### La detección automática de módulos usa plenamente `$env:PSModulePath` ###

La detección automática de módulos (carga de módulos automáticamente sin un cmdlet Import-Module explícito al llamar a un comando) se introdujo en WMF 3. Cuando se introdujo, PowerShell comprobaba los comandos en `$PSHome\Modules` antes de usar `$env:PSModulePath`.

WMF 5.1 cambia este comportamiento para usar `$env:PSModulePath` completamente. Esto permite que un módulo creado por el usuario que define los comandos que proporciona PowerShell (por ejemplo, `Get-ChildItem`) se cargue automáticamente y reemplace correctamente el comando integrado.

### El redireccionamiento de archivos deja de integrar como parte del código `-Encoding Unicode` ###

En todas las versiones anteriores de PowerShell, era imposible controlar la codificación de archivos utilizada por el operador de redireccionamiento de archivos (p. ej., `get-childitem > out.txt` porque PowerShell agregó `-Encoding Unicode`).

A partir de WMF 5.1, se puede cambiar la codificación de archivos del redireccionamiento mediante el establecimiento de `$PSDefaultParameterValues`, p. ej.

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### Se ha corregido una regresión en el acceso de los miembros de `System.Reflection.TypeInfo` ###

Una regresión introducida en WMF 5.0 interrumpía el acceso de los miembros de `System.Reflection.RuntimeType`, por ejemplo, `[int].ImplementedInterfaces`.
Este error se ha corregido en WMF 5.1.


### Se han corregido algunos problemas con objetos COM ###

WMF 5.0 introdujo un nuevo enlazador COM para invocar métodos en objetos COM y acceder a propiedades de objetos COM.
Este nuevo enlazador ha mejorado considerablemente el rendimiento, pero también ha presentado algunos errores que se han corregido en WMF 5.1.

#### Las conversiones de argumentos no siempre se realizaban correctamente ####

En el ejemplo siguiente:

```
$obj = new-object -com wscript.shell
$obj.SendKeys([char]173)
```

El método SendKeys espera una cadena, pero PowerShell no ha convertido el carácter en una cadena, lo que aplaza la conversión a IDispatch:: Invoke, que usa VariantChangeType para realizar la conversión, lo que en este ejemplo provocó el envío de las claves '1', '7' y '3', en lugar de la clave Volume.Mute, que era la que se esperaba.

#### Los objetos COM enumerables no siempre se controlan correctamente ####

PowerShell normalmente enumera la mayoría de los objetos enumerables, pero una regresión introducida en WMF 5.0 impidió la enumeración de objetos COM que implementan IEnumerable.  Por ejemplo:

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

En el ejemplo anterior, WMF 5.0 escribió incorrectamente Scripting.Dictionary en la canalización, en lugar de enumerar los pares clave/valor.

Este cambió también permite solucionar los [problemas 1752224 en Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)

### `[ordered]` no se permitía en las clases ###

WMF5 introdujo clases con una validación de los literales de tipo que se usan en las clases.  `[ordered]` parece un literal de tipo, pero no es un verdadero tipo .Net.  WMF5 informaba incorrectamente de un error en `[ordered]` dentro de una clase:

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

Get-Help no proporciona una forma de especificar para qué versión se desea la ayuda. Para solucionar este problema, navegue hasta el directorio modules y vea la ayuda directamente con una herramienta como su editor favorito. 



<!--HONumber=Jul16_HO3-->


