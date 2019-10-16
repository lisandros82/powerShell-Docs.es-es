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
# <a name="how-to-write-a-powershell-script-module"></a><span data-ttu-id="6e710-102">Cómo escribir un módulo de script de PowerShell</span><span class="sxs-lookup"><span data-stu-id="6e710-102">How to Write a PowerShell Script Module</span></span>

<span data-ttu-id="6e710-103">Un módulo de script es básicamente cualquier script de PowerShell válido guardado en una extensión. psm1.</span><span class="sxs-lookup"><span data-stu-id="6e710-103">A script module is essentially any valid PowerShell script saved in a .psm1 extension.</span></span> <span data-ttu-id="6e710-104">Esta extensión permite al motor de PowerShell usar una serie de reglas y cmdlets en el archivo.</span><span class="sxs-lookup"><span data-stu-id="6e710-104">This extension allows the PowerShell engine to use a number of rules and cmdlets on your file.</span></span> <span data-ttu-id="6e710-105">La mayoría de estas funcionalidades están allí para ayudarle a instalar el código en otros sistemas, así como para administrar el ámbito.</span><span class="sxs-lookup"><span data-stu-id="6e710-105">Most of these capabilities are there to help you install your code on other systems, as well as manage scoping.</span></span> <span data-ttu-id="6e710-106">También puede usar un archivo de manifiesto del módulo, que puede describir instalaciones y soluciones aún más complejas.</span><span class="sxs-lookup"><span data-stu-id="6e710-106">You can also use a module manifest file, which can describe even more complex installations and solutions.</span></span>

## <a name="writing-a-powershell-script-module"></a><span data-ttu-id="6e710-107">Escribir un módulo de script de PowerShell</span><span class="sxs-lookup"><span data-stu-id="6e710-107">Writing a PowerShell Script Module</span></span>

<span data-ttu-id="6e710-108">Para crear un módulo de script, guarde un script de PowerShell válido en un archivo. psm1 y, a continuación, guarde el archivo en un directorio donde pueda encontrarlo.</span><span class="sxs-lookup"><span data-stu-id="6e710-108">You create a script module by saving a valid PowerShell script to a .psm1 file, and then saving that file in a directory located where PowerShell can find it.</span></span> <span data-ttu-id="6e710-109">En esa carpeta también puede colocar cualquier recurso que necesite para ejecutar el script, así como un archivo de manifiesto que describa cómo funciona el módulo.</span><span class="sxs-lookup"><span data-stu-id="6e710-109">In that folder you can also place any resources you need to run your script, as well as a manifest file that describes to PowerShell how your module works.</span></span>

#### <a name="to-create-a-basic-powershell-module"></a><span data-ttu-id="6e710-110">Para crear un módulo básico de PowerShell</span><span class="sxs-lookup"><span data-stu-id="6e710-110">To create a basic PowerShell Module</span></span>

1. <span data-ttu-id="6e710-111">Tome un script de PowerShell existente y guarde el script con la extensión. psm1.</span><span class="sxs-lookup"><span data-stu-id="6e710-111">Take an existing PowerShell script, and save the script with a .psm1 extension.</span></span>

   <span data-ttu-id="6e710-112">Guardar un script con la extensión. psm1 significa que puede usar los cmdlets de módulo, como [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), en él.</span><span class="sxs-lookup"><span data-stu-id="6e710-112">Saving a script with the .psm1 extension means that you can use the module cmdlets, such as [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), on it.</span></span> <span data-ttu-id="6e710-113">Estos cmdlets existen principalmente para que pueda importar y exportar fácilmente el código en los sistemas de otros usuarios.</span><span class="sxs-lookup"><span data-stu-id="6e710-113">These cmdlets exist primarily so that you can easily import and export your code onto other user's systems.</span></span> <span data-ttu-id="6e710-114">(La solución alternativa sería cargar el código en otros sistemas y, a continuación, crear el origen de los mismos en la memoria activa, que no es una solución especialmente escalable). Para obtener más información, consulte la sección **cmdlets y variables de módulo** en [módulos de Windows PowerShell](./understanding-a-windows-powershell-module.md) . tenga en cuenta que, de forma predeterminada, todas las funciones del script son accesibles para los usuarios que importan el archivo. psm1, pero las propiedades no lo son.</span><span class="sxs-lookup"><span data-stu-id="6e710-114">(The alternate solution would be to load up your code on other systems and then dot-source it into active memory, which isn't a particularly scalable solution.) For more information see the **Module Cmdlets and Variables** section in [Windows PowerShell Modules](./understanding-a-windows-powershell-module.md) Note that, by default, all functions in your script are accessible to users who import your .psm1 file, but properties are not.</span></span>

   <span data-ttu-id="6e710-115">Al final de este tema encontrará un script de PowerShell de ejemplo, titulado `Show-Calendar`.</span><span class="sxs-lookup"><span data-stu-id="6e710-115">An example PowerShell script, entitled `Show-Calendar`, is available at the end of this topic.</span></span>

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

2. <span data-ttu-id="6e710-116">Para controlar el acceso de los usuarios a determinadas funciones o propiedades, llame a [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) al final del script.</span><span class="sxs-lookup"><span data-stu-id="6e710-116">To control user access to certain functions or properties, call [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) at the end of your script.</span></span>

   <span data-ttu-id="6e710-117">El código de ejemplo de la parte inferior de la página solo tiene una función, que de forma predeterminada se expondría.</span><span class="sxs-lookup"><span data-stu-id="6e710-117">The example code at the bottom of the page has only one function, which by default would be exposed.</span></span> <span data-ttu-id="6e710-118">Sin embargo, se recomienda que llame explícitamente a las funciones que desea exponer, como se describe en el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="6e710-118">However, it is recommended that you explicitly call out which functions you wish to expose, as described in the following code:</span></span>

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   <span data-ttu-id="6e710-119">También puede restringir lo que se importa mediante un manifiesto de módulo.</span><span class="sxs-lookup"><span data-stu-id="6e710-119">You can also restrict what is imported using a module manifest.</span></span> <span data-ttu-id="6e710-120">Para obtener más información, vea [importar un módulo de PowerShell](./importing-a-powershell-module.md) y [Cómo escribir un manifiesto del módulo de PowerShell](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="6e710-120">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [How to Write a PowerShell Module Manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

3. <span data-ttu-id="6e710-121">Si tiene módulos que su propio módulo necesita que se carguen, puede usarlos con una llamada a `Import-Module`, en la parte superior de su propio módulo.</span><span class="sxs-lookup"><span data-stu-id="6e710-121">If you have modules that your own module needs to have loaded, you can use them with a call to `Import-Module`, at the top of your own module.</span></span>

   <span data-ttu-id="6e710-122">`Import-Module` es un cmdlet que importa un módulo de destino en un sistema.</span><span class="sxs-lookup"><span data-stu-id="6e710-122">`Import-Module` is a cmdlet that imports a targeted module onto a system.</span></span> <span data-ttu-id="6e710-123">Por lo tanto, también se usa en un punto posterior del procedimiento para instalar su propio módulo.</span><span class="sxs-lookup"><span data-stu-id="6e710-123">As such, it is also used at a later point in the procedure to install your own module as well.</span></span> <span data-ttu-id="6e710-124">El código de ejemplo de la parte inferior de esta página no usa ningún módulo de importación.</span><span class="sxs-lookup"><span data-stu-id="6e710-124">The sample code at the bottom of this page does not use any import modules.</span></span> <span data-ttu-id="6e710-125">Sin embargo, si lo hiciera, se enumerarían en la parte superior del archivo, tal y como se describe en el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="6e710-125">If it did, however, they would be listed at the top of the file, as described in the following code:</span></span>

   ```powershell
   Import-Module GenericModule
   ```

4. <span data-ttu-id="6e710-126">Para describir el módulo en el sistema de ayuda de PowerShell, puede usar los comentarios de ayuda estándar dentro del archivo o crear un archivo de ayuda adicional.</span><span class="sxs-lookup"><span data-stu-id="6e710-126">To describe your module to the PowerShell Help system, you can either use standard help comments inside the file, or create an additional Help file.</span></span>

   <span data-ttu-id="6e710-127">En el ejemplo de código de la parte inferior de este tema se incluye la información de ayuda de los comentarios.</span><span class="sxs-lookup"><span data-stu-id="6e710-127">The code sample at the bottom of this topic includes the help information in the comments.</span></span> <span data-ttu-id="6e710-128">También puede escribir archivos XML expandidos que contengan contenido de ayuda adicional.</span><span class="sxs-lookup"><span data-stu-id="6e710-128">You could also write expanded XML files that contain additional help content.</span></span> <span data-ttu-id="6e710-129">Para obtener más información, vea [escribir ayuda para módulos de Windows PowerShell](./writing-help-for-windows-powershell-modules.md).</span><span class="sxs-lookup"><span data-stu-id="6e710-129">For more information, see [Writing Help for Windows PowerShell Modules](./writing-help-for-windows-powershell-modules.md).</span></span>

5. <span data-ttu-id="6e710-130">Si tiene módulos adicionales, archivos XML u otro contenido que desee empaquetar con el módulo, puede hacerlo con un manifiesto de módulo.</span><span class="sxs-lookup"><span data-stu-id="6e710-130">If you have additional modules, XML files, or other content you want to package up with your module, you can do so with a module manifest.</span></span>

   <span data-ttu-id="6e710-131">Un manifiesto de módulo es un archivo que contiene los nombres de otros módulos, diseños de directorio, números de control de versiones, datos de autor y otros tipos de información.</span><span class="sxs-lookup"><span data-stu-id="6e710-131">A module manifest is a file that contains the names of other modules, directory layouts, versioning numbers, author data, and other pieces of information.</span></span> <span data-ttu-id="6e710-132">PowerShell usa el archivo de manifiesto del módulo para organizar e implementar la solución.</span><span class="sxs-lookup"><span data-stu-id="6e710-132">PowerShell uses the module manifest file to organize and deploy your solution.</span></span> <span data-ttu-id="6e710-133">Sin embargo, debido a la naturaleza relativamente sencilla de este ejemplo, no era necesario un archivo de manifiesto.</span><span class="sxs-lookup"><span data-stu-id="6e710-133">However, due to the relatively simple nature of this example, a manifest file was not needed.</span></span> <span data-ttu-id="6e710-134">Para obtener más información, vea [manifiestos de módulo](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="6e710-134">For more information, see [Module Manifests](./how-to-write-a-powershell-module-manifest.md).</span></span>

6. <span data-ttu-id="6e710-135">Para instalar y ejecutar el módulo, guarde el módulo en una de las rutas de acceso de PowerShell apropiadas y realice una llamada a `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="6e710-135">To install and run your module, save the module to one of the appropriate PowerShell paths, and make a call to `Import-Module`.</span></span>

   <span data-ttu-id="6e710-136">Las rutas de acceso en las que puede instalar el módulo se encuentran en la variable global `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="6e710-136">The paths where you can install your module are located in the `$env:PSModulePath` global variable.</span></span> <span data-ttu-id="6e710-137">Por ejemplo, una ruta de acceso común para guardar un módulo en un sistema sería `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="6e710-137">For example, a common path to save a module on a system would be `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span></span> <span data-ttu-id="6e710-138">Asegúrese de crear una carpeta para que el módulo exista en, incluso si se trata de un único archivo. psm1.</span><span class="sxs-lookup"><span data-stu-id="6e710-138">Be sure to create a folder for your module to exist in, even if it is only a single .psm1 file.</span></span> <span data-ttu-id="6e710-139">Si no guardó el módulo en una de estas rutas de acceso, tendría que pasar la ubicación del módulo en la llamada a `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="6e710-139">If you did not save your module to one of these paths, you would have to pass in the location of your module in the call to `Import-Module`.</span></span> <span data-ttu-id="6e710-140">(De lo contrario, PowerShell no podría encontrarla). A partir de PowerShell 3,0, si ha colocado el módulo en una de las rutas de acceso del módulo de PowerShell, no es necesario importarlo explícitamente.</span><span class="sxs-lookup"><span data-stu-id="6e710-140">(Otherwise, PowerShell would not be able to find it.) Starting with PowerShell 3.0, if you have placed your module in one of the PowerShell module paths, you do not need to explicitly import it.</span></span> <span data-ttu-id="6e710-141">El módulo se carga automáticamente cuando un usuario llama a la función.</span><span class="sxs-lookup"><span data-stu-id="6e710-141">You module is automatically loaded when a user calls your function.</span></span>
   <span data-ttu-id="6e710-142">Para obtener más información sobre la ruta de acceso del módulo, vea [importar un módulo de PowerShell](./importing-a-powershell-module.md) y la [variable de entorno PSModulePath](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="6e710-142">For more information on the module path, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [PSModulePath Environment Variable](./modifying-the-psmodulepath-installation-path.md).</span></span>

7. <span data-ttu-id="6e710-143">Para quitar un módulo del servicio activo, realice una llamada a [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span><span class="sxs-lookup"><span data-stu-id="6e710-143">To remove a module from active service, make a call to [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span></span>

   <span data-ttu-id="6e710-144">Tenga en cuenta que [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) quita el módulo de la memoria activa, por lo que realmente no lo elimina de donde guardó los archivos de módulo.</span><span class="sxs-lookup"><span data-stu-id="6e710-144">Note that [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) removes your module from active memory - it does not actually delete it from where you saved the module files.</span></span>

### <a name="show-calendar-code-example"></a><span data-ttu-id="6e710-145">Ejemplo de código de mostrar calendario</span><span class="sxs-lookup"><span data-stu-id="6e710-145">Show-Calendar code example</span></span>

<span data-ttu-id="6e710-146">El ejemplo siguiente es un módulo de script simple que contiene una sola función denominada `Show-Calendar`.</span><span class="sxs-lookup"><span data-stu-id="6e710-146">The following example is a simple script module that contains a single function named `Show-Calendar`.</span></span>
<span data-ttu-id="6e710-147">Esta función muestra una representación visual de un calendario.</span><span class="sxs-lookup"><span data-stu-id="6e710-147">This function displays a visual representation of a calendar.</span></span> <span data-ttu-id="6e710-148">Además, el ejemplo contiene las cadenas de ayuda de PowerShell para la Sinopsis, la descripción, los valores de parámetro y el ejemplo.</span><span class="sxs-lookup"><span data-stu-id="6e710-148">In addition, the sample contains the PowerShell Help strings for the synopsis, description, parameter values, and example.</span></span> <span data-ttu-id="6e710-149">Tenga en cuenta que la última línea de código garantiza que la función `Show-Calendar` se exporte como un miembro del módulo cuando se importe el módulo.</span><span class="sxs-lookup"><span data-stu-id="6e710-149">Note that the last line of code ensures that the `Show-Calendar` function is exported as a module member when the module is imported.</span></span>

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
