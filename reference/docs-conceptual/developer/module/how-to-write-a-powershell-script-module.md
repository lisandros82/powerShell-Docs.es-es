---
title: Cómo escribir un módulo de script de PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: b2a929a1724f77f0516ad24cfd90f6d6053ed19e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360694"
---
# <a name="how-to-write-a-powershell-script-module"></a>Cómo escribir un módulo de script de PowerShell

Un módulo de script es básicamente cualquier script de PowerShell válido guardado en una extensión. psm1. Esta extensión permite al motor de PowerShell usar una serie de reglas y cmdlets en el archivo. La mayoría de estas funcionalidades están allí para ayudarle a instalar el código en otros sistemas, así como para administrar el ámbito. También puede usar un archivo de manifiesto del módulo, que puede describir instalaciones y soluciones aún más complejas.

## <a name="writing-a-powershell-script-module"></a>Escribir un módulo de script de PowerShell

Para crear un módulo de script, guarde un script de PowerShell válido en un archivo. psm1 y, a continuación, guarde el archivo en un directorio donde pueda encontrarlo. En esa carpeta también puede colocar cualquier recurso que necesite para ejecutar el script, así como un archivo de manifiesto que describa cómo funciona el módulo.

#### <a name="to-create-a-basic-powershell-module"></a>Para crear un módulo básico de PowerShell

1. Tome un script de PowerShell existente y guarde el script con la extensión. psm1.

   Guardar un script con la extensión. psm1 significa que puede usar los cmdlets de módulo, como [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), en él. Estos cmdlets existen principalmente para que pueda importar y exportar fácilmente el código en los sistemas de otros usuarios. (La solución alternativa sería cargar el código en otros sistemas y, a continuación, crear el origen de los mismos en la memoria activa, que no es una solución especialmente escalable). Para obtener más información, consulte la sección **cmdlets y variables de módulo** en [módulos de Windows PowerShell](./understanding-a-windows-powershell-module.md) . tenga en cuenta que, de forma predeterminada, todas las funciones del script son accesibles para los usuarios que importan el archivo. psm1, pero las propiedades no lo son.

   Al final de este tema encontrará un script de PowerShell de ejemplo, titulado `Show-Calendar`.

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

2. Para controlar el acceso de los usuarios a determinadas funciones o propiedades, llame a [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) al final del script.

   El código de ejemplo de la parte inferior de la página solo tiene una función, que de forma predeterminada se expondría. Sin embargo, se recomienda que llame explícitamente a las funciones que desea exponer, como se describe en el código siguiente:

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   También puede restringir lo que se importa mediante un manifiesto de módulo. Para obtener más información, vea [importar un módulo de PowerShell](./importing-a-powershell-module.md) y [Cómo escribir un manifiesto del módulo de PowerShell](./how-to-write-a-powershell-module-manifest.md).

3. Si tiene módulos que su propio módulo necesita que se carguen, puede usarlos con una llamada a `Import-Module`, en la parte superior de su propio módulo.

   `Import-Module` es un cmdlet que importa un módulo de destino en un sistema. Por lo tanto, también se usa en un punto posterior del procedimiento para instalar su propio módulo. El código de ejemplo de la parte inferior de esta página no usa ningún módulo de importación. Sin embargo, si lo hiciera, se enumerarían en la parte superior del archivo, tal y como se describe en el código siguiente:

   ```powershell
   Import-Module GenericModule
   ```

4. Para describir el módulo en el sistema de ayuda de PowerShell, puede usar los comentarios de ayuda estándar dentro del archivo o crear un archivo de ayuda adicional.

   En el ejemplo de código de la parte inferior de este tema se incluye la información de ayuda de los comentarios. También puede escribir archivos XML expandidos que contengan contenido de ayuda adicional. Para obtener más información, vea [escribir ayuda para módulos de Windows PowerShell](./writing-help-for-windows-powershell-modules.md).

5. Si tiene módulos adicionales, archivos XML u otro contenido que desee empaquetar con el módulo, puede hacerlo con un manifiesto de módulo.

   Un manifiesto de módulo es un archivo que contiene los nombres de otros módulos, diseños de directorio, números de control de versiones, datos de autor y otros tipos de información. PowerShell usa el archivo de manifiesto del módulo para organizar e implementar la solución. Sin embargo, debido a la naturaleza relativamente sencilla de este ejemplo, no era necesario un archivo de manifiesto. Para obtener más información, vea [manifiestos de módulo](./how-to-write-a-powershell-module-manifest.md).

6. Para instalar y ejecutar el módulo, guarde el módulo en una de las rutas de acceso de PowerShell apropiadas y realice una llamada a `Import-Module`.

   Las rutas de acceso en las que puede instalar el módulo se encuentran en la variable global `$env:PSModulePath`. Por ejemplo, una ruta de acceso común para guardar un módulo en un sistema sería `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`. Asegúrese de crear una carpeta para que el módulo exista en, incluso si se trata de un único archivo. psm1. Si no guardó el módulo en una de estas rutas de acceso, tendría que pasar la ubicación del módulo en la llamada a `Import-Module`. (De lo contrario, PowerShell no podría encontrarla). A partir de PowerShell 3,0, si ha colocado el módulo en una de las rutas de acceso del módulo de PowerShell, no es necesario importarlo explícitamente. El módulo se carga automáticamente cuando un usuario llama a la función.
   Para obtener más información sobre la ruta de acceso del módulo, vea [importar un módulo de PowerShell](./importing-a-powershell-module.md) y la [variable de entorno PSModulePath](./modifying-the-psmodulepath-installation-path.md).

7. Para quitar un módulo del servicio activo, realice una llamada a [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).

   Tenga en cuenta que [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) quita el módulo de la memoria activa, por lo que realmente no lo elimina de donde guardó los archivos de módulo.

### <a name="show-calendar-code-example"></a>Ejemplo de código de mostrar calendario

El ejemplo siguiente es un módulo de script simple que contiene una sola función denominada `Show-Calendar`.
Esta función muestra una representación visual de un calendario. Además, el ejemplo contiene las cadenas de ayuda de PowerShell para la Sinopsis, la descripción, los valores de parámetro y el ejemplo. Tenga en cuenta que la última línea de código garantiza que la función `Show-Calendar` se exporte como un miembro del módulo cuando se importe el módulo.

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
    $width = ($calendar.Split("`n") | Measure-Object -Maximum Length).Maximum
    $header = "{0:MMMM yyyy}" -f $start
    $padding = " " * (($width - $header.Length) / 2)
    $displayCalendar = " `n" + $padding + $header + "`n " + $calendar
    $displayCalendar.TrimEnd()

    ## Move to the next month.
    $start = $start.AddMonths(1)

}
}
Export-ModuleMember -Function Show-Calendar
```
