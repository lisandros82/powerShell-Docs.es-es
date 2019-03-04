---
title: Cómo escribir un módulo de Script de PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: e8b7151538235cdf7183b78aa8df7e596d6bcfd9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859011"
---
# <a name="how-to-write-a-powershell-script-module"></a>Cómo escribir un módulo de script de PowerShell

Un módulo de script es básicamente cualquier script de PowerShell válido guardado en una extensión. psm1. Esta extensión permite que el motor de PowerShell para usar una serie de reglas y los cmdlets en el archivo. La mayoría de estas capacidades sirven para ayudarle a instalar el código en otros sistemas, así como administrar el ámbito. También puede usar un archivo de manifiesto de módulo, que se puede describir aún más complejas instalaciones y las soluciones.

## <a name="writing-a-powershell-script-module"></a>Escribir un módulo de Script de PowerShell

Para crear un módulo de script, guardar un script de PowerShell válido en un archivo. psm1 y, a continuación, guardar el archivo en un directorio donde puede encontrar en PowerShell. En esa carpeta que también se pueden colocar los recursos que necesite para ejecutar el script, así como un archivo de manifiesto que describe a PowerShell cómo funciona el módulo.

#### <a name="to-create-a-basic-powershell-module"></a>Para crear un módulo de PowerShell básico

1. Tomar un script de PowerShell existente y guarde el script con la extensión. psm1.

   Guardar un script con el. psm1 extensión significa que puede usar los cmdlets del módulo, como [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), en él. Estos cmdlets existen principalmente para que se puede importar y exportar el código en sistemas de otros usuarios fácilmente. (La solución alternativa sería cargar el código en otros sistemas y, a continuación, punto de código en la memoria activa, lo cual no es una solución especialmente escalable). Para obtener más información, consulte el **Cmdlets del módulo y las Variables** sección [módulos de Windows PowerShell](./understanding-a-windows-powershell-module.md) tenga en cuenta que, de forma predeterminada, todas las funciones de la secuencia de comandos será accesibles a los usuarios que importación su. psm1 archivo, pero las propiedades no funcionará.

   Un ejemplo script de PowerShell, titulado Show-Calendar, está disponible al final de este tema.

   ```powershell
   function Show-Calendar {
   param(
       [DateTime] $start = [DateTime]::Today,
       [DateTime] $end = $start,
       $firstDayOfWeek,
       [int[]] $highlightDay,
       [string[]] $highlightDate = [DateTime]::Today.ToString()
       )

       #actual code for the function goes here see the end of the topic for the complete code sample
   }
   ```

2. Si desea controlar el acceso de usuario a ciertas propiedades o funciones, llamar a [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) al final de la secuencia de comandos.

   El código de ejemplo en la parte inferior de la página tiene solo una función, que se expondría de forma predeterminada. Sin embargo, se recomienda que se llame explícitamente a qué funciones desea exponer, tal como se describe en el código siguiente:

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   También puede restringir lo que se importa mediante un manifiesto de módulo. Para obtener más información, consulte [importar un módulo de PowerShell](./importing-a-powershell-module.md) y [cómo escribir un manifiesto del módulo de PowerShell](./how-to-write-a-powershell-module-manifest.md).

3. Si tiene módulos que se debe haber cargado su propio módulo, se puede usar con una llamada a `Import-Module`, en la parte superior de su propio módulo.

   `Import-Module` es un cmdlet que importa un módulo en un sistema de destino. Por lo tanto, también sirve en un momento posterior en el procedimiento para instalar su propio módulo también. El código de ejemplo en la parte inferior de esta página no usa los módulos de importación. Si lo hiciera, sin embargo, se muestran en la parte superior del archivo, como se describe en el código siguiente:

   ```powershell
   Import-Module GenericModule
   ```

4. Si desea describir el módulo en el sistema de Ayuda de PowerShell, puede hacerlo con los comentarios estándar ayuda dentro del archivo, o con un archivo de ayuda adicional.

   El ejemplo de código en la parte inferior de este tema incluye la información de ayuda en los comentarios. Si lo prefiere, también podría escribir archivos expandidos de XML que contienen el contenido de ayuda adicional. Para obtener más información, consulte [escribir ayuda para Windows PowerShell módulos](./writing-help-for-windows-powershell-modules.md).

5. Si tiene módulos adicionales, archivos XML u otro contenido que desea empaquetar con el módulo, puede hacerlo con un manifiesto de módulo.

   Un manifiesto de módulo es un archivo que contiene los nombres de otros módulos, los diseños de directorio, números de control de versiones, datos de autor y otros fragmentos de información. PowerShell usa el archivo de manifiesto de módulo para organizar e implementar la solución. Sin embargo, debido a la naturaleza relativamente sencilla de este ejemplo, un archivo de manifiesto no era necesario. Para obtener más información, consulte [manifiestos de módulo](./how-to-write-a-powershell-module-manifest.md).

6. Para instalar y ejecutar el módulo, guarde el módulo a una de las rutas adecuadas de PowerShell y realice una llamada a `Import-Module`.

   Las rutas de acceso donde puede instalar el módulo se encuentran en el `$env:PSModulePath` variable global. Por ejemplo, podría ser una ruta de acceso comunes para guardar un módulo en un sistema `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`. Asegúrese de crear una carpeta para el módulo exista, incluso si es sólo un archivo. psm1 único. Si no ha guardado el módulo a una de estas rutas de acceso, se tendría que pasar la ubicación del módulo en la llamada a `Import-Module`. (En caso contrario, PowerShell no sería capaz de encontrarlo.) A partir de PowerShell 3.0, si ha colocado el módulo en una de las rutas de acceso del módulo de PowerShell, no deberá importar de forma explícita: basta con tener un usuario llame a la función lo cargará automáticamente. Para obtener más información sobre la ruta de acceso del módulo, consulte [importar un módulo de PowerShell](./importing-a-powershell-module.md) y [Variable de entorno PSModulePath](./modifying-the-psmodulepath-installation-path.md).

7. Para quitar un módulo de servicio activo, realice una llamada a [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).

Tenga en cuenta que [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) quita el módulo desde la memoria activa - no elimina realmente, desde donde lo guardó los archivos de módulo.

### <a name="show-calendar-code-example"></a>Ejemplo de código Show-Calendar

El ejemplo siguiente es un módulo de script simple que contiene una sola función denominada Show-Calendar. Esta función muestra una representación visual de un calendario. Además, el ejemplo contiene las cadenas de Ayuda de PowerShell para la sinopsis, descripción, los valores de parámetro y ejemplo. Tenga en cuenta que la última línea de código indica que la función Show-Calendar se exportará como miembro de un módulo cuando se importa el módulo.

```powershell
<#
 .Synopsis
  Displays a visual representation of a calendar.

 .Description
  Displays a visual representation of a calendar. This function supports multiple months
  and lets you highlight specific date ranges or days.

 .Parameter Start
  The first month to display.

 .Parameter End
  The last month to display.

 .Parameter FirstDayOfWeek
  The day of the month on which the week begins.

 .Parameter HighlightDay
  Specific days (numbered) to highlight. Used for date ranges like (25..31).
  Date ranges are specified by the Windows PowerShell range syntax. These dates are
  enclosed in square brackets.

 .Parameter HighlightDate
  Specific days (named) to highlight. These dates are surrounded by asterisks.

 .Example
   # Show a default display of this month.
   Show-Calendar

 .Example
   # Display a date range.
   Show-Calendar -Start "March, 2010" -End "May, 2010"

 .Example
   # Highlight a range of days.
   Show-Calendar -HighlightDay (1..10 + 22) -HighlightDate "December 25, 2008"
#>
function Show-Calendar {
param(
    [DateTime] $start = [DateTime]::Today,
    [DateTime] $end = $start,
    $firstDayOfWeek,
    [int[]] $highlightDay,
    [string[]] $highlightDate = [DateTime]::Today.ToString()
    )

## Determine the first day of the start and end months.
$start = New-Object DateTime $start.Year,$start.Month,1
$end = New-Object DateTime $end.Year,$end.Month,1

## Convert the highlighted dates into real dates.
[DateTime[]] $highlightDate = [DateTime[]] $highlightDate

## Retrieve the DateTimeFormat information so that the
## calendar can be manipulated.
$dateTimeFormat  = (Get-Culture).DateTimeFormat
if($firstDayOfWeek)
{
    $dateTimeFormat.FirstDayOfWeek = $firstDayOfWeek
}

$currentDay = $start

## Process the requested months.
while($start -le $end)
{
    ## Return to an earlier point in the function if the first day of the month
    ## is in the middle of the week.
    while($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek)
    {
        $currentDay = $currentDay.AddDays(-1)
    }

    ## Prepare to store information about this date range.
    $currentWeek = New-Object PsObject
    $dayNames = @()
    $weeks = @()

    ## Continue processing dates until the function reaches the end of the month.
    ## The function continues until the week is completed with
    ## days from the next month.
    while(($currentDay -lt $start.AddMonths(1)) -or
        ($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek))
    {
        ## Determine the day names to use to label the columns.
        $dayName = "{0:ddd}" -f $currentDay
        if($dayNames -notcontains $dayName)
        {
            $dayNames += $dayName
        }

        ## Pad the day number for display, highlighting if necessary.
        $displayDay = " {0,2} " -f $currentDay.Day

        ## Determine whether to highlight a specific date.
        if($highlightDate)
        {
            $compareDate = New-Object DateTime $currentDay.Year,
                $currentDay.Month,$currentDay.Day
            if($highlightDate -contains $compareDate)
            {
                $displayDay = "*" + ("{0,2}" -f $currentDay.Day) + "*"
            }
        }

        ## Otherwise, highlight as part of a date range.
        if($highlightDay -and ($highlightDay[0] -eq $currentDay.Day))
        {
            $displayDay = "[" + ("{0,2}" -f $currentDay.Day) + "]"
            $null,$highlightDay = $highlightDay
        }

        ## Add the day of the week and the day of the month as note properties.
        $currentWeek | Add-Member NoteProperty $dayName $displayDay

        ## Move to the next day of the month.
        $currentDay = $currentDay.AddDays(1)

        ## If the function reaches the next week, store the current week
        ## in the week list and continue.
        if($currentDay.DayOfWeek -eq $dateTimeFormat.FirstDayOfWeek)
        {
            $weeks += $currentWeek
            $currentWeek = New-Object PsObject
        }
    }

    ## Format the weeks as a table.
    $calendar = $weeks | Format-Table $dayNames -AutoSize | Out-String

    ## Add a centered header.
    $width = ($calendar.Split("'n") | Measure-Object -Maximum Length).Maximum
    $header = "{0:MMMM yyyy}" -f $start
    $padding = " " * (($width - $header.Length) / 2)
    $displayCalendar = " 'n" + $padding + $header + "'n " + $calendar
    $displayCalendar.TrimEnd()

    ## Move to the next month.
    $start = $start.AddMonths(1)

}
}
Export-ModuleMember -Function Show-Calendar
```
