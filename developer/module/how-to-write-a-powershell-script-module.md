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
ms.openlocfilehash: b2a929a1724f77f0516ad24cfd90f6d6053ed19e
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470805"
---
# <a name="how-to-write-a-powershell-script-module"></a><span data-ttu-id="acb0f-102">Cómo escribir un módulo de script de PowerShell</span><span class="sxs-lookup"><span data-stu-id="acb0f-102">How to Write a PowerShell Script Module</span></span>

<span data-ttu-id="acb0f-103">Un módulo de script es básicamente cualquier script de PowerShell válido guardado en una extensión. psm1.</span><span class="sxs-lookup"><span data-stu-id="acb0f-103">A script module is essentially any valid PowerShell script saved in a .psm1 extension.</span></span> <span data-ttu-id="acb0f-104">Esta extensión permite que el motor de PowerShell para usar una serie de reglas y los cmdlets en el archivo.</span><span class="sxs-lookup"><span data-stu-id="acb0f-104">This extension allows the PowerShell engine to use a number of rules and cmdlets on your file.</span></span> <span data-ttu-id="acb0f-105">La mayoría de estas capacidades sirven para ayudarle a instalar el código en otros sistemas, así como administrar el ámbito.</span><span class="sxs-lookup"><span data-stu-id="acb0f-105">Most of these capabilities are there to help you install your code on other systems, as well as manage scoping.</span></span> <span data-ttu-id="acb0f-106">También puede usar un archivo de manifiesto de módulo, que se puede describir aún más complejas instalaciones y las soluciones.</span><span class="sxs-lookup"><span data-stu-id="acb0f-106">You can also use a module manifest file, which can describe even more complex installations and solutions.</span></span>

## <a name="writing-a-powershell-script-module"></a><span data-ttu-id="acb0f-107">Escribir un módulo de Script de PowerShell</span><span class="sxs-lookup"><span data-stu-id="acb0f-107">Writing a PowerShell Script Module</span></span>

<span data-ttu-id="acb0f-108">Para crear un módulo de script, guardar un script de PowerShell válido en un archivo. psm1 y, a continuación, guardar el archivo en un directorio donde puede encontrar en PowerShell.</span><span class="sxs-lookup"><span data-stu-id="acb0f-108">You create a script module by saving a valid PowerShell script to a .psm1 file, and then saving that file in a directory located where PowerShell can find it.</span></span> <span data-ttu-id="acb0f-109">En esa carpeta que también se pueden colocar los recursos que necesite para ejecutar el script, así como un archivo de manifiesto que describe a PowerShell cómo funciona el módulo.</span><span class="sxs-lookup"><span data-stu-id="acb0f-109">In that folder you can also place any resources you need to run your script, as well as a manifest file that describes to PowerShell how your module works.</span></span>

#### <a name="to-create-a-basic-powershell-module"></a><span data-ttu-id="acb0f-110">Para crear un módulo de PowerShell básico</span><span class="sxs-lookup"><span data-stu-id="acb0f-110">To create a basic PowerShell Module</span></span>

1. <span data-ttu-id="acb0f-111">Tomar un script de PowerShell existente y guarde el script con la extensión. psm1.</span><span class="sxs-lookup"><span data-stu-id="acb0f-111">Take an existing PowerShell script, and save the script with a .psm1 extension.</span></span>

   <span data-ttu-id="acb0f-112">Guardar un script con el. psm1 extensión significa que puede usar los cmdlets del módulo, como [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), en él.</span><span class="sxs-lookup"><span data-stu-id="acb0f-112">Saving a script with the .psm1 extension means that you can use the module cmdlets, such as [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), on it.</span></span> <span data-ttu-id="acb0f-113">Estos cmdlets existen principalmente para que se puede importar y exportar el código en sistemas de otros usuarios fácilmente.</span><span class="sxs-lookup"><span data-stu-id="acb0f-113">These cmdlets exist primarily so that you can easily import and export your code onto other user's systems.</span></span> <span data-ttu-id="acb0f-114">(La solución alternativa sería cargar el código en otros sistemas y, a continuación, punto de código en la memoria activa, lo cual no es una solución especialmente escalable). Para obtener más información, consulte el **Cmdlets del módulo y las Variables** sección [módulos de Windows PowerShell](./understanding-a-windows-powershell-module.md) tenga en cuenta que, de forma predeterminada, todas las funciones de la secuencia de comandos son accesibles a los usuarios que importación el archivo. psm1, pero no son de propiedades.</span><span class="sxs-lookup"><span data-stu-id="acb0f-114">(The alternate solution would be to load up your code on other systems and then dot-source it into active memory, which isn't a particularly scalable solution.) For more information see the **Module Cmdlets and Variables** section in [Windows PowerShell Modules](./understanding-a-windows-powershell-module.md) Note that, by default, all functions in your script are accessible to users who import your .psm1 file, but properties are not.</span></span>

   <span data-ttu-id="acb0f-115">Un ejemplo script de PowerShell, titulado `Show-Calendar`, está disponible al final de este tema.</span><span class="sxs-lookup"><span data-stu-id="acb0f-115">An example PowerShell script, entitled `Show-Calendar`, is available at the end of this topic.</span></span>

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

2. <span data-ttu-id="acb0f-116">Para controlar el acceso de usuario a ciertas propiedades o funciones, llamar a [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) al final de la secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="acb0f-116">To control user access to certain functions or properties, call [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) at the end of your script.</span></span>

   <span data-ttu-id="acb0f-117">El código de ejemplo en la parte inferior de la página tiene solo una función, que se expondría de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="acb0f-117">The example code at the bottom of the page has only one function, which by default would be exposed.</span></span> <span data-ttu-id="acb0f-118">Sin embargo, se recomienda que se llame explícitamente a qué funciones desea exponer, tal como se describe en el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="acb0f-118">However, it is recommended that you explicitly call out which functions you wish to expose, as described in the following code:</span></span>

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   <span data-ttu-id="acb0f-119">También puede restringir lo que se importa mediante un manifiesto de módulo.</span><span class="sxs-lookup"><span data-stu-id="acb0f-119">You can also restrict what is imported using a module manifest.</span></span> <span data-ttu-id="acb0f-120">Para obtener más información, consulte [importar un módulo de PowerShell](./importing-a-powershell-module.md) y [cómo escribir un manifiesto del módulo de PowerShell](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="acb0f-120">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [How to Write a PowerShell Module Manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

3. <span data-ttu-id="acb0f-121">Si tiene módulos que se debe haber cargado su propio módulo, se puede usar con una llamada a `Import-Module`, en la parte superior de su propio módulo.</span><span class="sxs-lookup"><span data-stu-id="acb0f-121">If you have modules that your own module needs to have loaded, you can use them with a call to `Import-Module`, at the top of your own module.</span></span>

   <span data-ttu-id="acb0f-122">`Import-Module` es un cmdlet que importa un módulo en un sistema de destino.</span><span class="sxs-lookup"><span data-stu-id="acb0f-122">`Import-Module` is a cmdlet that imports a targeted module onto a system.</span></span> <span data-ttu-id="acb0f-123">Por lo tanto, también sirve en un momento posterior en el procedimiento para instalar su propio módulo también.</span><span class="sxs-lookup"><span data-stu-id="acb0f-123">As such, it is also used at a later point in the procedure to install your own module as well.</span></span> <span data-ttu-id="acb0f-124">El código de ejemplo en la parte inferior de esta página no usa los módulos de importación.</span><span class="sxs-lookup"><span data-stu-id="acb0f-124">The sample code at the bottom of this page does not use any import modules.</span></span> <span data-ttu-id="acb0f-125">Si lo hiciera, sin embargo, se muestran en la parte superior del archivo, como se describe en el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="acb0f-125">If it did, however, they would be listed at the top of the file, as described in the following code:</span></span>

   ```powershell
   Import-Module GenericModule
   ```

4. <span data-ttu-id="acb0f-126">Para describir el módulo en el sistema de Ayuda de PowerShell, puede usar los comentarios de la Ayuda estándar dentro del archivo o crear un archivo de ayuda adicional.</span><span class="sxs-lookup"><span data-stu-id="acb0f-126">To describe your module to the PowerShell Help system, you can either use standard help comments inside the file, or create an additional Help file.</span></span>

   <span data-ttu-id="acb0f-127">El ejemplo de código en la parte inferior de este tema incluye la información de ayuda en los comentarios.</span><span class="sxs-lookup"><span data-stu-id="acb0f-127">The code sample at the bottom of this topic includes the help information in the comments.</span></span> <span data-ttu-id="acb0f-128">También podría escribir archivos expandidos de XML que contienen el contenido de ayuda adicional.</span><span class="sxs-lookup"><span data-stu-id="acb0f-128">You could also write expanded XML files that contain additional help content.</span></span> <span data-ttu-id="acb0f-129">Para obtener más información, consulte [escribir ayuda para Windows PowerShell módulos](./writing-help-for-windows-powershell-modules.md).</span><span class="sxs-lookup"><span data-stu-id="acb0f-129">For more information, see [Writing Help for Windows PowerShell Modules](./writing-help-for-windows-powershell-modules.md).</span></span>

5. <span data-ttu-id="acb0f-130">Si tiene módulos adicionales, archivos XML u otro contenido que desea empaquetar con el módulo, puede hacerlo con un manifiesto de módulo.</span><span class="sxs-lookup"><span data-stu-id="acb0f-130">If you have additional modules, XML files, or other content you want to package up with your module, you can do so with a module manifest.</span></span>

   <span data-ttu-id="acb0f-131">Un manifiesto de módulo es un archivo que contiene los nombres de otros módulos, los diseños de directorio, números de control de versiones, datos de autor y otros fragmentos de información.</span><span class="sxs-lookup"><span data-stu-id="acb0f-131">A module manifest is a file that contains the names of other modules, directory layouts, versioning numbers, author data, and other pieces of information.</span></span> <span data-ttu-id="acb0f-132">PowerShell usa el archivo de manifiesto de módulo para organizar e implementar la solución.</span><span class="sxs-lookup"><span data-stu-id="acb0f-132">PowerShell uses the module manifest file to organize and deploy your solution.</span></span> <span data-ttu-id="acb0f-133">Sin embargo, debido a la naturaleza relativamente sencilla de este ejemplo, un archivo de manifiesto no era necesario.</span><span class="sxs-lookup"><span data-stu-id="acb0f-133">However, due to the relatively simple nature of this example, a manifest file was not needed.</span></span> <span data-ttu-id="acb0f-134">Para obtener más información, consulte [manifiestos de módulo](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="acb0f-134">For more information, see [Module Manifests](./how-to-write-a-powershell-module-manifest.md).</span></span>

6. <span data-ttu-id="acb0f-135">Para instalar y ejecutar el módulo, guarde el módulo a una de las rutas adecuadas de PowerShell y realice una llamada a `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="acb0f-135">To install and run your module, save the module to one of the appropriate PowerShell paths, and make a call to `Import-Module`.</span></span>

   <span data-ttu-id="acb0f-136">Las rutas de acceso donde puede instalar el módulo se encuentran en el `$env:PSModulePath` variable global.</span><span class="sxs-lookup"><span data-stu-id="acb0f-136">The paths where you can install your module are located in the `$env:PSModulePath` global variable.</span></span> <span data-ttu-id="acb0f-137">Por ejemplo, podría ser una ruta de acceso comunes para guardar un módulo en un sistema `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="acb0f-137">For example, a common path to save a module on a system would be `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span></span> <span data-ttu-id="acb0f-138">Asegúrese de crear una carpeta para el módulo exista, incluso si es sólo un archivo. psm1 único.</span><span class="sxs-lookup"><span data-stu-id="acb0f-138">Be sure to create a folder for your module to exist in, even if it is only a single .psm1 file.</span></span> <span data-ttu-id="acb0f-139">Si no ha guardado el módulo a una de estas rutas de acceso, se tendría que pasar la ubicación del módulo en la llamada a `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="acb0f-139">If you did not save your module to one of these paths, you would have to pass in the location of your module in the call to `Import-Module`.</span></span> <span data-ttu-id="acb0f-140">(En caso contrario, PowerShell no sería capaz de encontrarlo.) A partir de PowerShell 3.0, si ha colocado el módulo en una de las rutas de acceso del módulo de PowerShell, es necesario importar de forma explícita.</span><span class="sxs-lookup"><span data-stu-id="acb0f-140">(Otherwise, PowerShell would not be able to find it.) Starting with PowerShell 3.0, if you have placed your module in one of the PowerShell module paths, you do not need to explicitly import it.</span></span> <span data-ttu-id="acb0f-141">Módulo se carga automáticamente cuando un usuario llama a la función.</span><span class="sxs-lookup"><span data-stu-id="acb0f-141">You module is automatically loaded when a user calls your function.</span></span>
   <span data-ttu-id="acb0f-142">Para obtener más información sobre la ruta de acceso del módulo, consulte [importar un módulo de PowerShell](./importing-a-powershell-module.md) y [Variable de entorno PSModulePath](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="acb0f-142">For more information on the module path, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [PSModulePath Environment Variable](./modifying-the-psmodulepath-installation-path.md).</span></span>

7. <span data-ttu-id="acb0f-143">Para quitar un módulo de servicio activo, realice una llamada a [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span><span class="sxs-lookup"><span data-stu-id="acb0f-143">To remove a module from active service, make a call to [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span></span>

   <span data-ttu-id="acb0f-144">Tenga en cuenta que [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) quita el módulo desde la memoria activa - no elimina realmente, desde donde lo guardó los archivos de módulo.</span><span class="sxs-lookup"><span data-stu-id="acb0f-144">Note that [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) removes your module from active memory - it does not actually delete it from where you saved the module files.</span></span>

### <a name="show-calendar-code-example"></a><span data-ttu-id="acb0f-145">Ejemplo de código Show-Calendar</span><span class="sxs-lookup"><span data-stu-id="acb0f-145">Show-Calendar code example</span></span>

<span data-ttu-id="acb0f-146">El ejemplo siguiente es un módulo de script simple que contiene una sola función denominada `Show-Calendar`.</span><span class="sxs-lookup"><span data-stu-id="acb0f-146">The following example is a simple script module that contains a single function named `Show-Calendar`.</span></span>
<span data-ttu-id="acb0f-147">Esta función muestra una representación visual de un calendario.</span><span class="sxs-lookup"><span data-stu-id="acb0f-147">This function displays a visual representation of a calendar.</span></span> <span data-ttu-id="acb0f-148">Además, el ejemplo contiene las cadenas de Ayuda de PowerShell para la sinopsis, descripción, los valores de parámetro y ejemplo.</span><span class="sxs-lookup"><span data-stu-id="acb0f-148">In addition, the sample contains the PowerShell Help strings for the synopsis, description, parameter values, and example.</span></span> <span data-ttu-id="acb0f-149">Tenga en cuenta que la última línea de código garantiza que el `Show-Calendar` función se exporta como miembro de un módulo cuando se importa el módulo.</span><span class="sxs-lookup"><span data-stu-id="acb0f-149">Note that the last line of code ensures that the `Show-Calendar` function is exported as a module member when the module is imported.</span></span>

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
